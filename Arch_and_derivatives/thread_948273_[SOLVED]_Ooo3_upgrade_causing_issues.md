---
title: "[SOLVED] Ooo3 upgrade causing issues"
date: 2008-10-15
forum: Arch and derivatives
---

### Post by kpkeerthi on 2008-10-15
Upgraded the new ooo3 package from extra. But when I open Writer (or any other Ooo application) all I get is a File Recovery window. Ooo3 prompts me to recover the files listed but there is nothing in the list. All I can do from here is click on 'Start Recovery' and it takes me back to same screen and I keep looping over and over. 

I found ~/.openoffice and ~/.openoffice2 folders and I tried removing them but still no luck.

Does anybody have a clue or having the problem?

---

### Post by kpkeerthi on 2008-10-15
[This]("http://bugs.archlinux.org/task/11705?project=1") could be it. I'm not in front of Arch right now to check and confirm. I'm running Openbox so I'm hoping the issue is the same as described in the bug. Can't wait to check it out.

---

### Post by randy78 on 2008-10-15
After going around and around in the document recovery loop/crash with the newest OpenOffice (3), I have decided to document my steps and post the resolution in hopes that it will help many of our Linux brethren :)

I went through the following:
Completely uninstalled OpenOffice 2 and the installation of OpenOffice 3
I installed OpenOffice 3 (sudo dpkg -i *.deb) from within the DEBS folder
I then installed desktop integration from the desktop-integration folder

I renamed .openoffice.org2 to openoffice.org2.backup

I deleted the Recovery.xcu file

I did: OOO_FORCE_DESKTOP=gnome

When I'd start OpenOffice from shell (soffice) and (soffice -writer), it immediately went right into Document Recovery mode and gave this output in Bash:
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'

I also had made sure that the .openoffice and .openoffice2 folders were not owned by root

Finally, I found this post:[http://www.nabble.com/-Linux--OOo3RC2-Installation-Issues-Workaround-td19695985.html]("http://www.nabble.com/-Linux--OOo3RC2-Installation-Issues-Workaround-td19695985.html")

I followed the instructions (deleted .openoffice.org folder and renamed .openoffice.org2.backup back to .openoffice.org2)

*note that these folders are hidden by default in your home directory, so once you're there just press control+h to show the hidden files ;)

Works like a charm now.

WHOOHOOO!

Hoped this helps some people!
:guitar:

---

### Post by Odd-rationale on 2008-10-15
Same issue. Installing libxslt solved I for me. (as i am the one who started the forum thread in the bug report... :P)

be sure you are also setting the environment variable: [http://wiki.archlinux.org/index.php/OpenOffice#Set_OOo_environment_variable](http://wiki.archlinux.org/index.php/OpenOffice#Set_OOo_environment_variable)

---

### Post by kpkeerthi on 2008-10-15
Fixed. Installed libxslt.

---

