---
title: "Help Installing Thrid Party Software"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by metsfan47 on 2007-12-10
Hey everyone, 

I've been using Ubuntu for a few months now and loving it.  My biggest challenge thus far has been installing third party software.  I downloaded Galleon (Tivo Software for those of you not familiar with it) and extracted the files.  Then, using terminal I changed my directory to where I had the files saved and typed "sudo make install" and this is what happened

install -d /usr/share/galleon
install -d /var/cache/galleon
install -d /etc/galleon
install -d /usr/lib/galleon
install -d /var/log/galleon
install -d /var/lib/galleon/hme
install -d /var/lib/galleon/data
cp -rf bin media /usr/share/galleon
cp -f Makefile COPYING *.txt /usr/share/galleon
cp -f conf/*.* /etc/galleon
cp -rf lib/* /usr/lib/galleon
cp -rf apps skins /var/lib/galleon
cp -rf conf/templates /var/lib/galleon
chmod a+rwx /usr/share/galleon/bin/run.sh
chmod a+rwx /usr/share/galleon/bin/gui.sh
chmod a+rwx /usr/share/galleon/bin/galleon
chmod a+rwx /usr/share/galleon/bin/wrapper*
chmod +rw /etc/galleon/configure.xml
ln -sf /var/lib/galleon/apps /usr/share/galleon/apps
ln -sf /etc/galleon /usr/share/galleon/conf
ln -sf /var/lib/galleon/data /usr/share/galleon/data
ln -sf /var/lib/galleon/hme /usr/share/galleon/hme 
ln -sf /usr/lib/galleon /usr/share/galleon/lib
ln -sf /var/log/galleon /usr/share/galleon/logs 
ln -sf /var/lib/galleon/skins /usr/share/galleon/skins
ln -sf /var/lib/galleon/templates /etc/galleon/templates
ln -sf /usr/share/galleon/bin/galleon /etc/init.d/galleon
chkconfig --add galleon
make: chkconfig: Command not found
make: *** [install] Error 127

If anyone can tell me what I'm doing wrong, I would appreciate it.  Thanks in advance everyone!!

-Aaron

---

### Post by LaRoza on 2007-12-10
Did you configure it? There is probably a read me file in the directory, read it first.

Also, for compiling:

```

sudo aptitude install build-essential

```

---

### Post by metsfan47 on 2007-12-10
I did read the readme file, but all it says is see "makefile" in this directory.  I don't really understand makefile.  It says:

# $Id: Makefile,v 1.5 2007/09/28 17:03:37 s2kdave Exp $
#
#  Makefile for Galleon 2.x
#
# --
#
#


#
#  Installation Directories.
#
APPDIR      = /usr/share/galleon
CACHEDIR    = /var/cache/galleon
CONFDIR     = /etc/galleon
LIBDIR      = /usr/lib/galleon
LOGDIR      = /var/log/galleon
VARDIR      = /var/lib/galleon


#
#  Default target, give the user some help.
#
a:
	@echo "galleon 2.x Makefile"
	@echo ""
	@echo " Available targets (alphabetically):"
	@echo "    make install   - Install the software in ${APPDIR}."
	@echo "    make uninstall - Removes this software completely."
	@echo "    make upgrade   - Install the software in ${APPDIR} while saving the configure.xml that is currently installed."
	@echo " "
	@echo " For more details see:"
	@echo "    http://galleon.tv/"
	@echo " "

install:
	install -d ${APPDIR}
	install -d ${CACHEDIR}
	install -d ${CONFDIR}
	install -d ${LIBDIR}
	install -d ${LOGDIR}
	install -d ${VARDIR}/hme
	install -d ${VARDIR}/data
	cp -rf bin media ${APPDIR}
	cp -f Makefile COPYING *.txt ${APPDIR}
	cp -f conf/*.* ${CONFDIR}
	cp -rf lib/* ${LIBDIR}
	cp -rf apps skins ${VARDIR}
	cp -rf conf/templates ${VARDIR}
	chmod a+rwx ${APPDIR}/bin/run.sh
	chmod a+rwx ${APPDIR}/bin/gui.sh
	chmod a+rwx ${APPDIR}/bin/galleon
	chmod a+rwx ${APPDIR}/bin/wrapper*
	chmod +rw ${CONFDIR}/configure.xml
	ln -sf ${VARDIR}/apps ${APPDIR}/apps
	ln -sf ${CONFDIR} ${APPDIR}/conf
	ln -sf ${VARDIR}/data ${APPDIR}/data
	ln -sf ${VARDIR}/hme ${APPDIR}/hme 
	ln -sf ${LIBDIR} ${APPDIR}/lib
	ln -sf ${LOGDIR} ${APPDIR}/logs 
	ln -sf ${VARDIR}/skins ${APPDIR}/skins
	ln -sf ${VARDIR}/templates ${CONFDIR}/templates
	ln -sf ${APPDIR}/bin/galleon /etc/init.d/galleon
	chkconfig --add galleon

uninstall:
	chkconfig --del galleon
	rm -f ${APPDIR}/apps
	rm -f ${APPDIR}/conf
	rm -f ${APPDIR}/data
	rm -f ${APPDIR}/hme
	rm -f ${APPDIR}/lib
	rm -f ${APPDIR}/logs
	rm -f ${APPDIR}/skins
	rm -f ${CONFDIR}/templates
	rm -f /etc/init.d/galleon
	-rm -rf ${CONFDIR}
	-rm -rf ${LOGDIR}
	-rm -rf ${CACHEDIR}
	-rm -rf ${LIBDIR}
	-rm -rf ${VARDIR}
	-rm -rf ${APPDIR}

backup:
	cp -f ${CONFDIR}/configure.xml /tmp/configure.xml.save
	
restore:
	mv -f /tmp/configure.xml.save ${CONFDIR}/configure.xml
	
upgrade: backup uninstall install restore

I don't understand any of that.  

I tried installing build essentials earlier today and just again now, and it runs a bunch of stuff then says 

0% waiting for headers

and never gets any farther than that.  

-Aaron

---

### Post by cibmal on 2008-01-12
I just hit the same problems you did with chkconfig, which doesn't seem to be an Ubuntu utility.  It seems the analogous command is update-rc.d, 

Take a look at [http://galleon.tv/component/option,com_joomlaboard/Itemid,26/func,view/id,901/catid,9/](http://galleon.tv/component/option,com_joomlaboard/Itemid,26/func,view/id,901/catid,9/)

If you have run "sudo make install" already you should pretty much be set to follow the directions in that post to get Galleon up and running.  You'll likely just need to adjust the script for the correct JAVA_HOME and the correct GALLEON_HOME.  Then install that script into /etc/init.d and run update-rc.d against it if you desire.

---

### Post by shinson71 on 2008-03-26
> **cibmal said:**
> I just hit the same problems you did with chkconfig, which doesn't seem to be an Ubuntu utility.  It seems the analogous command is update-rc.d, 

Take a look at [http://galleon.tv/component/option,com_joomlaboard/Itemid,26/func,view/id,901/catid,9/](http://galleon.tv/component/option,com_joomlaboard/Itemid,26/func,view/id,901/catid,9/)

If you have run "sudo make install" already you should pretty much be set to follow the directions in that post to get Galleon up and running.  You'll likely just need to adjust the script for the correct JAVA_HOME and the correct GALLEON_HOME.  Then install that script into /etc/init.d and run update-rc.d against it if you desire.

Can anyone translate the above into lowly "windows user" mode. Okay, I downloaded galleon, extracted it to my documents folder, installed java JRE, and now i am lost on what all the script adjustment rhetoric is. I did try the sudo make install and got the same result as the two gentlemen above. Any help would be appreciated.

---

### Post by Ocyberbum on 2008-04-15
same here i have been trying to install this or anything that could work but i end up with an error:
install -d /usr/share/galleon
install -d /var/cache/galleon
install -d /etc/galleon
install -d /usr/lib/galleon
install -d /var/log/galleon
install -d /var/lib/galleon/hme
install -d /var/lib/galleon/data
cp -rf bin media /usr/share/galleon
cp -f Makefile COPYING *.txt /usr/share/galleon
cp -f conf/*.* /etc/galleon
cp -rf lib/* /usr/lib/galleon
cp -rf apps skins /var/lib/galleon
cp -rf conf/templates /var/lib/galleon
chmod a+rwx /usr/share/galleon/bin/run.sh
chmod a+rwx /usr/share/galleon/bin/gui.sh
chmod a+rwx /usr/share/galleon/bin/galleon
chmod a+rwx /usr/share/galleon/bin/wrapper*
chmod +rw /etc/galleon/configure.xml
ln -sf /var/lib/galleon/apps /usr/share/galleon/apps
ln -sf /etc/galleon /usr/share/galleon/conf
ln -sf /var/lib/galleon/data /usr/share/galleon/data
ln -sf /var/lib/galleon/hme /usr/share/galleon/hme
ln -sf /usr/lib/galleon /usr/share/galleon/lib
ln -sf /var/log/galleon /usr/share/galleon/logs
ln -sf /var/lib/galleon/skins /usr/share/galleon/skins
ln -sf /var/lib/galleon/templates /etc/galleon/templates
ln -sf /usr/share/galleon/bin/galleon /etc/init.d/galleon
chkconfig --add galleon
make: chkconfig: Command not found
make: *** [install] Error 127

I installed  Java jre and did the build-essential but it errors out, i came accross some post saying that chkconfig was not used by ubuntu so im stuck..im using kubuntu hardy beta. I did find 2 vlc plugins but i have not had any luck with them either
libvstream_plugin.so & libty_plugin.so

---

### Post by seahills on 2008-06-08
<chkconfig --add galleon
<make: chkconfig: Command not found
<make: *** [install] Error 127

make is calling the chkconfig command to install the init script, but that doesn't exist on your system.  With debian, update-rc.d is used instead. Type 'update-rc.d galleon defaults' at the cli and the script will install into /etc/init.d/

-or- 'apt-get install rcconf' and then run 'rcconf' and check the galleon service.  

Once the script has installed into /etc/init.d/  the galleon server will start at boot. To start it without rebooting do '/etc/init.d/galleon start' at the prompt.

---

