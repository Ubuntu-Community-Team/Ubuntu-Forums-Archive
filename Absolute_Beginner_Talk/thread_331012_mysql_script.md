---
title: "mysql script"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by LookTJ on 2007-01-04
By accident, I deleted mysql script from /etc/init.d

How do I recover

I typed sudo rm -rf /etc/init.d/mysql

that **was** by **accident**


things I tried[LIST]
[*]reinstall everything mysql related[/LIST]

---

### Post by moephan on 2007-01-04
I dunno if this will help, but here's mine:

```

#!/bin/bash
#
# MySQL daemon start/stop script.
#
# Debian version. Based on the original by TcX.
#
set -e
set -u
${DEBIAN_SCRIPT_DEBUG:+ set -v -x}

test -x /usr/sbin/mysqld || exit 0

SELF=$(cd $(dirname $0); pwd -P)/$(basename $0)
CONF=/etc/mysql/my.cnf
MYADMIN="/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf"

# priority can be overriden and "-s" adds output to stderr
ERR_LOGGER="logger -p daemon.err -t /etc/init.d/mysql -i"

# Safeguard (relative paths, core dumps..)
cd /
umask 077

# mysqladmin likes to read /root/.my.cnf. This is usually not what I want
# as many admins e.g. only store a password without a username there and
# so break my scripts.
export HOME=/etc/mysql/

## Fetch a particular option from mysql's invocation.
#
# Usage: void mysqld_get_param option
mysqld_get_param() {
        /usr/sbin/mysqld --print-defaults \
                | tr " " "\n" \
                | grep -- "--$1" \
                | tail -n 1 \
                | cut -d= -f2
}

## Do some sanity checks before even trying to start mysqld.
sanity_checks() {
  # check for config file
  if [ ! -r /etc/mysql/my.cnf ]; then
    /bin/echo "WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz" | $ERR_LOGGER -s
  fi

  datadir=`mysqld_get_param datadir`
  if LC_ALL=C BLOCKSIZE= df --portability $datadir/. | tail -n 1 | awk '{ exit ($4>4096) }'; then
    /bin/echo "ERROR: The partition with $datadir is too full!" | $ERR_LOGGER -s    exit 1
  fi
}

## Checks if there is a server running and if so if it is accessible.
#
# check_alive insists on a pingable server
# check_dead also fails if there is a lost mysqld in the process list
#
# Usage: boolean mysqld_status [check_alive|check_dead] [warn|nowarn]
mysqld_status () {
    ping_output=`$MYADMIN ping 2>&1`; ping_alive=$(( ! $? ))

    ps_alive=0
    pidfile=`mysqld_get_param pid-file`
    if [ -f "$pidfile" ] && ps `cat $pidfile` >/dev/null 2>&1; then ps_alive=1; fi

    if [ "$1" = "check_alive"  -a  $ping_alive = 1 ] ||
       [ "$1" = "check_dead"   -a  $ping_alive = 0  -a  $ps_alive = 0 ]; then
        return 0 # EXIT_SUCCESS
    else
        if [ "$2" = "warn" ]; then
            /bin/echo -e "$ps_alive processes alive and '$MYADMIN ping' resulted in\n$ping_output\n" | $ERR_LOGGER -p daemon.debug
        fi
        return 1 # EXIT_FAILURE
    fi
}

#
# main()
#

case "${1:-''}" in
  'start')
        sanity_checks;
        # Start daemon
        echo -n "Starting MySQL database server: mysqld"
        if mysqld_status check_alive nowarn; then
           echo "...already running."
        else
            /usr/bin/mysqld_safe > /dev/null 2>&1 &
            # 6s was reported in #352070 to be too few when using ndbcluster
            for i in 1 2 3 4 5 6 7 8 9 10 11 12 13 14; do
                sleep 1
                if mysqld_status check_alive nowarn ; then break; fi
                echo "."
            done
            if mysqld_status check_alive warn; then
                echo "."
                # Now start mysqlcheck or whatever the admin wants.
                /etc/mysql/debian-start
            else
                echo "...failed or took more than 6s."
                /bin/echo -e "\tPlease take a look at the syslog."
            fi
        fi

        # Some warnings
        if $MYADMIN variables | egrep -q have_bdb.*YES; then
            /bin/echo "BerkeleyDB is obsolete, see /usr/share/doc/mysql-server-5.0/README.Debian.gz" | $ERR_LOGGER -p daemon.info
        fi
        if [ -f /etc/mysql/debian-log-rotate.conf ]; then
            /bin/echo "/etc/mysql/debian-log-rotate.conf is obsolete, see /usr/share/doc/mysql-server-5.0/NEWS.Debian.gz" | $ERR_LOGGER -p daemon.info
        fi
        ;;

  'stop')
        # * As a passwordless mysqladmin (e.g. via ~/.my.cnf) must be possible
        # at least for cron, we can rely on it here, too. (although we have
        # to specify it explicit as e.g. sudo environments points to the normal
        # users home and not /root)
        echo -n "Stopping MySQL database server: mysqld"
        if ! mysqld_status check_dead nowarn; then
          set +e
          shutdown_out=`$MYADMIN shutdown 2>&1`; r=$?
          set -e
          if [ "$r" -ne 0 ]; then
            /bin/echo -e -n "...failed.\n$shutdown_out\nKilling MySQL database server by signal: mysqld"
            killall -15 mysqld
            server_down=
            for i in 1 2 3 4 5 6 7 8 9 10; do
              sleep 1
              if mysqld_status check_dead nowarn; then server_down=1; break; fi
            done
          if test -z "$server_down"; then killall -9 mysqld; fi
          fi
        fi

        if ! mysqld_status check_dead warn; then
          echo "...failed."
          echo "Please stop MySQL manually and read /usr/share/doc/mysql-server-5.0/README.Debian.gz!"
          exit -1
        else
          echo "."
        fi
        ;;

  'restart')
        set +e; $SELF stop; set -e
        $SELF start
        ;;

  'reload'|'force-reload')
        echo -n "Reloading MySQL database server: mysqld"
        $MYADMIN reload
        echo "."
        ;;

  'status')
        if mysqld_status check_alive nowarn; then
          $MYADMIN version
        else
          echo "MySQL is stopped."
          exit 3
        fi
        ;;

  *)
        echo "Usage: $SELF start|stop|restart|reload|force-reload|status"
        exit 1
        ;;
esac

```

---

### Post by LookTJ on 2007-01-04
> **moephan said:**
> I dunno if this will help, but here's mine

Thank you for your copy, Resolved!

---

