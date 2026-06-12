---
title: "How to remove programs manually?"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by raul_ on 2006-09-29
This may be a noob question, but how do i remove a program i installed manually? with manually i mean not installed with apt-get but from a .rpm file or something like that. By removing only the folder, am i not leaving things behind?

---

### Post by Anonii on 2006-09-29
I dont really know about .rpm, come on we are a Debian-based distro :P

But about tarballs, if you kept the file-tree from where you installed it (did the "make install") you can get in that directory and use the command "make uninstall"

Good luck <:

---

### Post by pseudonym on 2006-09-29
If by 'installed manually' you also mean with 'sudo dpkg -i <package_name>.deb', such programs are still within package management and can be uninstalled via synaptic or 'sudo apt-get --purge remove'.

If you installed some 3rd-party driver (eg. nvidia) they usually come with an uninstall script. If said script fails they usually print a log file to /var/log which contains the list of files it tried unsuccessfully to remove. In such cases you can just delete each of those files manually to get rid of the program.

---

### Post by raul_ on 2006-09-30
ok i'll explain better. i installed firefox manually because my repositories didn't have the latest version. now i updated do dapper and i want to install the version from the repositories again, so it's easier to update and install plugins. the thing is, i installed firefox from the repositories, removed the "custom" directory, and now when i start firefox something strange happened. first i started from the terminal, and a "raw" firefox started. no themes no nothing. a bit later, i started from the panel ( i didn't remove the icon from the old firefox) and the themed firefox started. so i went to the terminal again, typed "firefox" and the themed started again, instead of the "raw". i tried to watch videos on youtube but it says that the latest version of the flash player isn't installed but i never had that problem before....i installed the flash player manually, but the error still appears...by the way, i linked "firefox" command to my old firefox path..

sorry if it seems confusing :(

---

### Post by easyease on 2006-09-30
Hmm im not sure what the problem is but this page may be of use.....
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5)
look about halfway down there is a script to install the latest firefox.the article is pretty in depth so it may at least give you a clue.

---

### Post by easyease on 2006-09-30
ok ill cut and paste the bit that seems relevent thanks to the original writer!
"Install Firefox 1.5

Firefox updates for Ubuntu Breezy 5.10 come rather slow, since Breezy is no longer a priority. You can either wait, and in the meantime be susceptible to those security holes, or install the official mozilla release instead. (While updates for Dapper are reasonably fast, they are still a few days behind the official mozilla release, so you may want to do this on Dapper as well.) Lucky for us, it is quite simple to do. This page on the Ubuntu wiki spills the beans on how to get the new firefox going.

As an alternative to following the wiki instructions, you can use this script that will automatically download and install the new firefox for you. I created it in collaboration with Aysiu, who helped with testing, ideas, and motivation. It automatically detects the newest firefox release, allows you to make a choice of language for firefox, verifies the gpg signature, and installs the new firefox in /opt/firefox. Here are the steps to take to use this script:

    * Download the script to your desktop
    * Open a terminal (how?)
    * Enter these commands: 

cd Desktop
chmod +x installnewfirefox.sh
./installnewfirefox.sh

And, if no errors occur, your new firefox is ready for use!

A few little tricks:

    * If middle click on tab to close it does not work, you can enable it by pointing Firefox to "about:config" and set middleclick.contentloadURL to false. Voila, middle click to close works again.
    * To enable the autoscroll (where you middle click and a little arrow-graphic appears and you can scroll just by moving the mouse), go to "about:config" and set general.autoScroll to true.
    * To automatically select the entire contents of the URL bar when you click there, open "about:config" and set browser.urlbar.clickSelectsAll to true. I find this a helpful usability improvement. 

Update Firefox 1.5.0.x to any later version

Since we installed the "non-ubuntu" version of firefox, above, in order to update it, we have to use the native firefox updater, rather than the apt-get method. In order for firefox to update itself, though, it will have to be run as root. So quit all firefox windows, and in a terminal, type:

gksudo firefox &

This will start firefox as root. Select Help>Check for Updates from the menu, and it will find an update, and download it. You will then get a message that says that Firefox needs to be restarted to apply the update, and you can choose "Later" or "Restart Firefox Now". DO NOT choose "Restart Firefox Now", instead DO choose "Later". (If you choose restart now, then firefox will close, and restart itself - but when it restarts it will no longer be running as root, and the update will fail.) Then close firefox yourself, and in a terminal again issue:

gksudo firefox &

This will restart firefox as root, and successfully complete the update. Now, you can close firefox again, and then start it as normal from the menu, not as root. And you should be all good to go! "

---

### Post by raul_ on 2006-09-30
Thanks for your work :) the thing is..i already have the latest firefox. i'll try to explain it better.

when i was in breezy, i installed firefox 1.5 manually, because my repositories had an old version.
now i upgraded to dapper, and i decided to replace my version with the one in the repositories (the version is the same, but the locations where they install are different). 
why did i do this? so my packet manager would notify me of updates.
anyway, i installed via apt-get, and removed the directory where i had my firefox installed (/firefox). but now, i get this strange error on youtube, saying that i don't have the latest flash player installed, and i followed their instructions twice, but no good.

---

### Post by easyease on 2006-09-30
ok so you have firefox, did you try re instaling the flash plug-in?

 sudo update-flashplugin

if not that then you may have to manually install it from scratch, as explained near the bottom of this page.......

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by raul_ on 2006-09-30
well, that didn't work :( i changed the subject to the other thread because this has nothing to do with the title :P lol thanks for ur replies

---

### Post by easyease on 2006-09-30
This will make most sites think you are running version 9 in Ubuntu even if you are not.
Don't forget to copy/backup the file before editing it.

sudo gedit ~/.mozilla/firefox/pluginreg.dat

change
Shockwave Flash 7.0 r63:$
to
Shockwave Flash 9.0 r63:$
 
 save, restart firefox.

---

### Post by raul_ on 2006-09-30
check the other thread m8 ;)

---

