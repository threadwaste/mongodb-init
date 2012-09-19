mongodb-init
============

A mongod init script that supports multiple instances on the same host, and handles NUMA placement policy where applicable.  It's main goal is to accommodate arbiters co-hosted with actual mongod nodes and sandboxed development nodes.

Usage
=====

	Usage: mongod {restart|start|status|stop} [instance]

Configuration
=============

By default, the script will act against all valid instances.  Actions can be optionally targetted.  For the purposes of this script, an instance is identified by a directory under $INSTANCE_ROOT that contains a file $CNF_FILE.  By default:

	$INSTANCE_ROOT=/etc/mongod
	$CNF_FILE=mongod.cnf

Thus, a file /etc/mongod/mongo1/mongod.cnf would result in an instance, mongo1.

	$ /etc/init.d/mongod status mongo1
	mongo1: mongod (pid  20472) is running.
