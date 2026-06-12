---
title: "Can anyone remote desktop to fix a MySQL socket error?  Will Paypal $15"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by justin4480 on 2007-10-29
I am having the following error output when running a php script when connecting to my phpMyAdmin MySQL database:

Debug Warning: /var/www/jwgodfrey/include.php line 28 - mysql_connect() [<a href='function.mysql-connect'>function.mysql-connect</a>]: Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)

I am not being lazy, I have spend a couple of hours forum searching and trying suggestions from previous posts to no avail.

If anyone could remote desktop connect and fix this for me I would very grateful.  I know the forum help for newbies isn't about money, but would be more than happy to pay $15 via paypal to anyone who can help.

I assume remote desktop connection to a laptop running Ubuntu isn't a problem, but I'm only assuming this.

---

### Post by llamakc on 2007-10-29
sudo /etc/init.d/mysql start

and try again.

---

### Post by justin4480 on 2007-10-29
thanks for the advice llamakc... Just tried that, made no difference.

---

### Post by justin4480 on 2007-10-29
FYI.

root@justin:/home/justin# sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                 [ OK ] 
root@justin:/home/justin#

---

### Post by llamakc on 2007-10-29
Is MySQL running? Either open System > Administration > System Monitor and go to the "Processes" tab. You'll have to click VIEW and check "All processes". Look for MySQL.

That or from the commandline type:

```

ps aux | grep mysql

```Also, have you installed libapache2-mod-auth-mysql and php5-mysql yet?

```

sudo apt-get install libapache2-mod-auth-mysql php5-mysql

```

Then restart Apache.

```

sudo apache2ctl restart

```

And try again.

---

### Post by justin4480 on 2007-10-29
I can see 2 mysql related processes running:
mysqld
mysqld_safe

root@justin:/home/justin# ps aux | grep mysql
root      5246  0.0  0.0   1756   532 ?        S    20:00   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     5286  0.0  0.7 127036 16448 ?        Sl   20:00   0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      5287  0.0  0.0   1676   548 ?        S    20:00   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root     12830  0.0  0.0   2992   784 pts/0    R+   23:20   0:00 grep mysql

I am not sure if libapache2-mod-auth-mysql is installed.  To be honest, I'm not sure what it is.  I have installed phpMyAdmin only.

---

### Post by llamakc on 2007-10-29
IF you installed phpmyadmin from Synaptic or with apt-get from the Ubuntu repositories, it would have installed those packages for you as phpmyadmin depends on them.

So, how did you install phpmyadmin?

---

### Post by justin4480 on 2007-10-29
Sorry, missed the second part of your post..  Just run the command...

Setting up libapache2-mod-auth-mysql (4.3.9-4) ...
root@justin:/home/justin# sudo apache2ctl restart
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.0.99 for ServerName

Still failing with same error when running php mysql db_connect() script.

---

### Post by justin4480 on 2007-10-29
I did install via synaptic, and have just marked for reinstallation.  That ran and completed fine, but error persists.

---

### Post by llamakc on 2007-10-29
Somebody more knowledgeable may have to help you. I see that in the OP the script is saying it can't connect to mysql.sock in /tmp, however MY mysql.sock is in /var/run/mysqld (and MySQL works fine on my machine).

Perhaps you could post part of the code that is failing? If not, you may have to ask this in the programming forum here to get a better answer or further help.

---

### Post by justin4480 on 2007-10-29
//-----------LOCAL-----------
@define ("DBHOST", "localhost");
@define ("DBNAME", "jwgodfrey");
@define ("DBUSER", "root@localhost");
@define ("DBPASS", "*********");

// Database connect function
function db_connect($dbname = DBNAME, $dbuser = DBUSER, $dbpass = DBPASS, $dbhost = DBHOST)
{
    $conn = @mysql_connect($dbhost, $dbuser, $dbpass) or DIE("DATABASE CONNECTION ERROR");
    @mysql_select_db($dbname, $conn);
    return $conn;
}

echo array_query("SELECT fname FROM details WHERE *");

---

### Post by justin4480 on 2007-10-29
hmmm...  My mysqld.sock file is also in /var/run/mysqld/mysqld.sock

However I do seem to have another copy in /tmp, although I think that is just a link to the above directory

---

### Post by llamakc on 2007-10-29
Where did you get the /var/www/USER/include.php file from?

---

### Post by justin4480 on 2007-10-29
That is the script I'm running and is failing (the extract of code I posted).

I wrote it on for a previous project, which was a fully working script.

---

### Post by llamakc on 2007-10-29
Huhm, this one may be beyond me. I didn't realize you could put the DBUSER with 'localhost' in the same line. I've always separated the dbuser and dbhost.

You also said in the OP that you were trying to connect to the phpMyadmin database. Did you mean another database?

---

### Post by justin4480 on 2007-10-29
phpMyAdmin is the tool I use to administor (create/edit) my MySQL database(s).

Don't worry...  I'll battle on.

Thanks very much for your help llamakc.

---

### Post by llamakc on 2007-10-29
No, I know what phpmyadmin is, and I have it successfully installed. PHPMyAdmin works successfully for you, right?

Are you certain this is correct?

@define ("DBUSER", "root@localhost");

shouldn't it be ("DBUSER", "root");

What sort of system was this working on before?

---

### Post by justin4480 on 2007-10-29
Simular setup, php4 and MySQL but running on Suse (a year back).

I think root@localhost does works, but just to be sure I have just changed and tried @define ("DBUSER", "root") but same issue.

---

### Post by llamakc on 2007-10-29
What's on line 28 of the code?

---

### Post by justin4480 on 2007-10-29
phpMyAdmin appears to be working fine.  I can login and create/edit databases and tables.

From the forum search's I've done, simular problems have been related to the paths outline in the my.cnf file.

---

### Post by justin4480 on 2007-10-29
25 // Database connect function
26 function db_connect($dbname = DBNAME, $dbuser = DBUSER, $dbpass = DBPASS, $dbhost = DBHOST)
27 {
28    $conn = @mysql_connect($dbhost, $dbuser, $dbpass) or DIE("DATABASE CONNECTION ERROR");
29     @mysql_select_db($dbname, $conn);
30    return $conn;
31 }

---

### Post by justin4480 on 2007-10-29
is a remote desktop possible?

---

### Post by llamakc on 2007-10-29
When you connect to the script from Firefox are you typing in:

localhost or your LAN IP?

---

### Post by justin4480 on 2007-10-29
I'm running it from Zend Studio 5.5.0

---

