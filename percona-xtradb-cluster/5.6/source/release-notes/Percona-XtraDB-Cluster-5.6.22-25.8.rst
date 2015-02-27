.. rn:: 5.6.22-25.8

======================================
 |Percona XtraDB Cluster| 5.6.22-25.8 
======================================

Percona is glad to announce the release of |Percona XtraDB Cluster| 5.6 on March 3rd 2015. Binaries are available from `downloads area <http://www.percona.com/downloads/Percona-XtraDB-Cluster-56/release-5.6.22-25.8/>`_ or from our :doc:`software repositories </installation>`.

Based on `Percona Server 5.6.22-72.0 <http://www.percona.com/doc/percona-server/5.6/release-notes/Percona-Server-5.6.22-72.0.html>`_ including all the bug fixes in it, `Galera Replicator 3.9 <https://github.com/codership/galera/issues?q=milestone%3A25.3.9>`_ and on `Codership wsrep API 25.8 <https://launchpad.net/codership-mysql/+milestone/5.6.21-25.8>`_ is now the current **General Availability** release. All of |Percona|'s software is open-source and free, all the details of the release can be found in the `5.6.22-25.8 milestone <https://launchpad.net/percona-xtradb-cluster/+milestone/5.6.22-25.8>`_ at Launchpad.

Bugs fixed 
==========

 :ref:`xtrabackup_sst` wouldn't stop when |MySQL| was ``SIGKILLed``. This would prevent |MySQL| to initiate a new transfer as port 4444 was already utilized. Bug fixed :bug:`1380697`.

 :file:`wsrep_sst_xtrabackup-v2` script was causing |innobackupex| to print a false positive stack trace into the log. Bug fixed :bug:`1407599`.

 |MyISAM| DDL (``CREATE/DROP``) isn't replicated any more when :variable:`wsrep-replicate-myisam` is ``OFF``. Bug fixed :bug:`1402338`.

 :variable:`gcache.mem_size` has been deprecated. A warning will now be generated if the variable has value different than ``0``. Bug fixed :bug:`1392408`.

  ``stderr`` of SST/Innobackupex is logged to syslog with appropriate tags if ``sst-syslog`` is in ``[sst]`` or ``[mysqld_safe]`` has syslog. This can be overriden by setting the :variable:`sst-syslog` to ``-1`` in ``[sst]``). Bug fixed :bug:`1399134`.

 ``clustercheck`` can now check if the node is ``PRIMARY`` or not. Bug fixed :bug:`1403566`.

 |SST| will now fail early if the :file:`xtrabackup_checkpoints` is missing on the joiner side. Bug fixed :bug:`1405985`.

 ``socat`` utility was not properly terminated after a timeout. Bug fixed :bug:`1409710`.

 When started (without bootstrap), the node would hang if it couldn't find primary node. Bug fixed :bug:`1413258`.

 10 seconds timeout in :ref:`xtrabackup_sst` script was not enough for the joiner to delete existing files before it started the socat receiver on systems with big ``datadir``. Bug fixed :bug:`1413879`.

 Non booststrap node could crash while attempting to perform ``table%cache`` operations. Bug fixed :bug:`1414635`.

 |Percona XtraDB Cluster| 5.6 would crash on ``ALTER TABLE`` / ``CREATE INDEX`` due to ?????. Bug fixed :bug:`1282707`.

 Variable length arrays in WSREP code were causing debug builds to fail. Bug fixed :bug:`1409042`.

 Race condition between donor and joiner in :ref:`xtrabackup_sst` has been fixed. Bug fixed :bug:`1405668`.

Other bugs fixed: :bug:`1399175`, :bug:`1382797`, :bug:`1275814` 

Help us improve quality by reporting any bugs you encounter using our `bug tracking system <https://bugs.launchpad.net/percona-xtradb-cluster/+filebug>`_. As always, thanks for your continued support of Percona!

