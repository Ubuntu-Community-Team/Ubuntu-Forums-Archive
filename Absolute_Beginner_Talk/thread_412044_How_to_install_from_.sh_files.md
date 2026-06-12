---
title: "How to install from .sh files"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by AdrenalineJunkie on 2007-04-17
Basicly i was wondering how you are meant to deal with the '.sh' files.

When i try to open it, it says;


Could not open 'file-name-here'

The pacakge might be corrupted or you are not allowed to open the file. Check permissions of the file.


I have checked the permissions and i have Read and Write privileges.

Thanks in advance.

---

### Post by Cypher on 2007-04-17
.SH files are "shell" files that can be executed if you have something like "#!/bin/sh" or something in the first line. So for starters, add Execute priv's to the file and see if you have better luck.

If that doesn't work, then open up a Terminal and try "sh <file.sh>"...

Regards

---

### Post by sh4d3z on 2007-04-17
you need to have execute permissions check the box that say execute as a program or do a chmod u+x filename.sh from the CLI

---

### Post by annda on 2007-04-17
hi!

you need execute rights and the file needs to be executable. did the file have no accompanying guide?

you need to type this in the **terminal** to make the file executable:
```

chmod +x filename
```

or even 

```
sudo chmod +x filename
```

after that, navigate to the directory and run it by:
```

./filename
```

or

```
sh filename.sh
```

---

### Post by AdrenalineJunkie on 2007-04-17
Its still not working, i guess im doing something really silly wrong and ill kick myself when i realise.

If it helps at all, the file im using is here [http://www.jahshaka.org/component/option,com_docman/task,cat_view/gid,42/Itemid,49/]("http://www.jahshaka.org/component/option,com_docman/task,cat_view/gid,42/Itemid,49/")

---

### Post by Cypher on 2007-04-17
Can you paste the contents of the .SH file to [Pastebin]("http://pastebin.com/") so we can see it? 

Regards

---

### Post by AdrenalineJunkie on 2007-04-17
```
#!/usr/bin/env sh

function dapper_register( ) {
	[ "`grep repo.jahshaka.org/ubuntu/dapper /etc/apt/sources.list`" = "" ] &&
	echo deb http://repo.jahshaka.org/ubuntu/dapper/ binary-i386/ >> /etc/apt/sources.list
	apt-get --quiet update 2>&1 > /dev/null
	return $?
}

function dapper_simulate( ) {
	apt-get --simulate install $* 2>&1
	return $?
}

function dapper_install( ) {
	apt-get --force-yes --yes install $*
	return $?
}

function change_user( ) {
	zenity --question --text "Welcome to the Jahshaka Ubuntu Installer.\n\nShould you wish to continue, I will need your password."
	[ $? = 0 ] && packages=`chmod +x $1 && gksudo $1 install`
	for i in $packages
	do
		(
			echo [Desktop Entry]
			echo Type=Application
			echo Name=$i
			echo TryExec=$i
			echo Exec=$i
		) > $HOME/Desktop/$i.desktop
	done
}

function install( ) {
	info=`$register` && [ $? != 0 ] && zenity --error --text "$info" && exit

	packages=`zenity --list --checklist --separator=" " --column "Download" --column "Package" $available`
	[ "$packages" = "" ] && zenity --error --text "No packages selected." && exit

	info=`$simulate $packages`
	if [ $? = 0 ] 
	then
		zenity  --question --title "Jahshaka"  --text "$info"
		[ $? = 0 ] && ( $installs $packages | zenity --progress --pulsate ) &&
		packages=`echo $packages | sed 's/openlibraries-media//'` &&
		[ "$packages" != "" ] &&
		zenity --question --text="Installation complete.\n\nDo you want me to create desktop icons for those applications?" &&
		echo $packages
	else
		zenity --error --text "$info"
	fi
}

if [ "$1" != "install" ]
then 
	( [ -f "/etc/issue" ] && uname -m | grep "i.86" && cat /etc/issue | grep "6\.06" ) > /dev/null
	if [ $? == 0 ]
	then change_user $0
	else zenity --error --text "This script only applies to Ubuntu 6.06 x86 32 bit platforms."
	fi
else
	export available="TRUE jahshaka TRUE jahplayer TRUE jplayer FALSE openlibraries-media"
	export register="dapper_register"
	export simulate="dapper_simulate"
	export installs="dapper_install"
	install
fi



```

---

### Post by annda on 2007-04-17
what error do you get?

i get:
jahshaka-dapper-x86.sh: 3: Syntax error: "(" unexpected

there seems something wrong with the installer script...

---

### Post by Cypher on 2007-04-17
Can you execute the command "env sh" in a Terminal and show us what it says?

---

### Post by AdrenalineJunkie on 2007-04-17
I just cant seem to execute it.

and when i run 'env sh'

the terminal just lets me write '$'

Is there a way around this script not working, or is it a bit of a lost cause?

---

### Post by Cypher on 2007-04-17
OK..type this
```

which bash

```
If that responds with "/usr/bin/bash", then change the "#!/usr/bin/env sh" with just "#!/usr/bin/bash" and the script should execute fine.

Regards

---

### Post by AdrenalineJunkie on 2007-04-18
Im sorry to say, i give up.

It doesn't really seem worth it for one piece of software, i shall find an alternative.

Thanks for your help world.

---

### Post by westdan2 on 2007-04-19
I would like to install this and i'm not getting anywhere.  I changed it to #!/usr/bin/bash but then it gives me :

bad interpreter: no such file or directory

---

### Post by digitalloving on 2007-09-16
I have ubuntu 7.04 "the feisty fawn" and attempted to install jahshaka as well.  The script failed on my computer with the error message

./jahshaka-dapper-x86.sh: 3: Syntax error: "(" unexpected

I chmodded the script to have execute privs and ran as super user.  The command /usr/bin/env sh drops me into an bash environment like it is designed to do.  I'm not certain why this is failing.  

That being said, the path, on my installation of Ubuntu, for bash is /bin/bash.  If I remove the /usr/bin/env sh and replace it is /bin/bash the script runs without a problem.  However, because the script does a check for Ubuntu 6.06 and I have Ubuntu 7.04 it tells me that it won't work.

Thankfully, the script is smarter than I am for trying to get it to work.  Essentially, all the script does is add a dapper drake repository and then tell Ubuntu to install jahshaka.  

While I'll probably have to install this from source, I wanted post this for the good of the community.  For those who just want the simple steps.

1.Check that you have ubuntu 6.06
2.Download the Jahshaka install .sh file
3.chmod +x jahshaka-dapper-x86.sh
4.Edit the file and change "/usr/bin/env sh" to "/bin/bash"
5.sudo ./jahshaka-dapper-x86.sh
6.eat a sandwich..if you're hungry and you like to eat sandwiches.

---

