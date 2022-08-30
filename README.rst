==============================
REANA Authentication Rucio
==============================

.. image:: https://github.com/reanahub/reana-auth-rucio/workflows/CI/badge.svg
   :target: https://github.com/reanahub/reana-auth-rucio/actions

.. image:: https://badges.gitter.im/Join%20Chat.svg
   :target: https://gitter.im/reanahub/reana?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge

.. image:: https://img.shields.io/github/license/reanahub/reana-auth-rucio.svg
   :target: https://github.com/reanahub/reana-auth-rucio/blob/master/LICENSE

About
=====

``reana-auth-rucio`` provides a container image for creating the right Rucio configuration.
The container image includes no additional logic or libraries,
just the bare minimum to support Rucio. The image is configured to support authentication
for the four experiments at CERN's Large Hadron Collider (ALICE, ATLAS, CMS, LHCb),
as well as `ESCAPE <https://projectescape.eu/>`_ Virtual Organization.

``reana-auth-rucio`` was developed for use in the `REANA
<http://www.reana.io/>`_ reusable research data analysis platform.

Usage
=====

You can use ``reana-auth-rucio`` as a base image, however it was built
to be used as a sidecar container with the single purpose of creating the right Rucio configuration.
Once obtained, the configuration files are shared with the main container using common namespaces.

The end users can ask for Rucio support by means of declaring `rucio: true`. Currently, the container
requires VOMS authentication meaning that `voms_proxy: true` has also to be declared, enabling the
`reana-auth-vomsproxy <https://github.com/reanahub/reana-auth-vomsproxy>`_ sidecar container.

Inside the container Rucio commands can be executed, for example via:

.. code-block:: console

  $ rucio whoami

Dependencies
=============

Running the container and successfully obtaining Rucio configuration requires additional information:

- ``CERN-bundle.pem``, downloaded from `Rucio GitLab repo <https://gitlab.cern.ch/plove/rucio/-/tree/master/etc/web>`_
- ``EGI-trustanchors.repo``, curled from `EGI Community repository <https://repository.egi.eu/sw/production/cas/1/current/repo-files/EGI-trustanchors.repo>`_

Changes
=======

Version 1.0.0 (UNRELEASED)
--------------------------

- Initial release

Development
===========

You can build the ``reana-auth-rucio`` image by optionally passing the build arguments
``BASETAG`` in order to specify the tag of ``rucio/rucio-clients``.

More information
================

For more information about `REANA <https://www.reana.io/>`_ reusable research
data analysis platform, please see `its documentation <https://docs.reana.io/>`_.

Contributors
============

The list of contributors in alphabetical order:

- `Agisilaos Kounelis <https://orcid.org/0000-0001-9312-3189>`_
- `Elena Gazzarrini <https://orcid.org/0000-0001-5772-5166>`_
- `Tibor Simko <https://orcid.org/0000-0001-7202-5803>`_