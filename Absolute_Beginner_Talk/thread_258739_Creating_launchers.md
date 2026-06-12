---
title: "Creating launchers"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by locoHost on 2006-09-16
I have a .sh file in /usr/shared/datastudio. When I go to the folder using nautilus and doubleclick the .sh file, the app starts fine. I copied the .sh file to my desktop and doubleclick it, and nothing happens. I guess I'm not sure how to make app launchers on the desktop. Obviously ;-)

Here is the .sh file contents...

#!/bin/sh
#SET ADS_HOME to the root installation directory for DataStudio

ADS_HOME=`/usr/share/datastudio`

CLASSES=$ADS_HOME/lib/ads.jar
CLASSES=$ADS_HOME/lib/aqua-lib.jar:$CLASSES
CLASSES=$ADS_HOME/lib/oracle.jar:$CLASSES
CLASSES=$ADS_HOME/lib/nlscharset12.jar:$CLASSES
CLASSES=$ADS_HOME/lib/jtds.jar:$CLASSES
CLASSES=$ADS_HOME/lib/mysql.jar:$CLASSES
CLASSES=$ADS_HOME/lib/postgresql.jar:$CLASSES
CLASSES=$ADS_HOME/lib/jnlp.jar:$CLASSES
CLASSES=$ADS_HOME/lib/db2java.jar:$CLASSES
CLASSES=$ADS_HOME/lib/db2jcc.jar:$CLASSES
CLASSES=$ADS_HOME/lib/db2jcc_license_cu.jar:$CLASSES
CLASSES=$ADS_HOME/lib/ifxjdbc.jar:$CLASSES
CLASSES=$ADS_HOME/lib/jconnect55.jar:$CLASSES
CLASSES=$ADS_HOME/lib/jconnect60.jar:$CLASSES
CLASSES=$ADS_HOME/lib/xdb.jar:$CLASSES
CLASSES=$ADS_HOME/lib/xmlparserv2.jar:$CLASSES

java -cp $CLASSES com.aquafold.datastudio.DataStudio


Is there something there that is preventing it from launching from my desktop? How can I put a launcher for DataStudio on my desktop?

Thanks sharing your expertise :-)

---

### Post by asplode on 2006-09-16
Make a link to the sh file, and copy the link to your desktop.

---

### Post by locoHost on 2006-09-16
Doesn't work. Doubleclick the new link on the desktop and nothing happens.

---

### Post by ToniWiki on 2007-04-03
Try adding at the beginning of the script a "cd /usr/shared/datastudio" line. Something like this:

```

#!/bin/sh
#SET ADS_HOME to the root installation directory for DataStudio


cd /usr/share/datastudio
ADS_HOME=`/usr/share/datastudio`

CLASSES=$ADS_HOME/lib/ads.jar
CLASSES=$ADS_HOME/lib/aqua-lib.jar:$CLASSES
CLASSES=$ADS_HOME/lib/oracle.jar:$CLASSES
CLASSES=$ADS_HOME/lib/nlscharset12.jar:$CLASSES
CLASSES=$ADS_HOME/lib/jtds.jar:$CLASSES
CLASSES=$ADS_HOME/lib/mysql.jar:$CLASSES
CLASSES=$ADS_HOME/lib/postgresql.jar:$CLASSES
CLASSES=$ADS_HOME/lib/jnlp.jar:$CLASSES
CLASSES=$ADS_HOME/lib/db2java.jar:$CLASSES
CLASSES=$ADS_HOME/lib/db2jcc.jar:$CLASSES
CLASSES=$ADS_HOME/lib/db2jcc_license_cu.jar:$CLASSES
CLASSES=$ADS_HOME/lib/ifxjdbc.jar:$CLASSES
CLASSES=$ADS_HOME/lib/jconnect55.jar:$CLASSES
CLASSES=$ADS_HOME/lib/jconnect60.jar:$CLASSES
CLASSES=$ADS_HOME/lib/xdb.jar:$CLASSES
CLASSES=$ADS_HOME/lib/xmlparserv2.jar:$CLASSES

java -cp $CLASSES com.aquafold.datastudio.DataStudio

```

Then create a launcher to the script in Desktop or where you want.

It worked for me. :)

---

