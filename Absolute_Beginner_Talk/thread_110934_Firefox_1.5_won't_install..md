---
title: "Firefox 1.5 won't install."
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by endangst on 2006-01-01
Hi everyone.  I followed the instructions at FirefoxNewVersion, step by step, but this is what happens:
 
endangst@ubuntu:~$ cd ~/.mozilla/firefox/*.default
[email]endangst@ubuntu:~/.mozilla/firefox/j5rzlk0s.defa[/email]ult$ mkdir ~/Desktop/ffsettings
mkdir: cannot create directory `/home/endangst/Desktop/ffsettings': File exists
[email]endangst@ubuntu:~/.mozilla/firefox/j5rzlk0s.defa[/email]ult$ cp bookmarks.html cert8.db cookies.txt formhistory.dat key3.db signons.txt history.dat  mimeTypes.rdf ~/Desktop/ffsettings
[email]endangst@ubuntu:~/.mozilla/firefox/j5rzlk0s.defa[/email]ult$ sudo cp firefox-1.5.tar.gz /opt/
Password:
cp: cannot stat `firefox-1.5.tar.gz': No such file or directory
[email]endangst@ubuntu:~/.mozilla/firefox/j5rzlk0s.defa[/email]ult$ cd ..
[email]endangst@ubuntu:~/.mozi[/email]lla/firefox$ cd ..
[email]endangst@ubuntu:~/.mozi[/email]lla$ cd ..
endangst@ubuntu:~$ sudo cp firefox-1.5.tar.gz /opt/
cp: cannot stat `firefox-1.5.tar.gz': No such file or directory
endangst@ubuntu:~$ ls
Desktop
endangst@ubuntu:~$ cd desktop
bash: cd: desktop: No such file or directory
endangst@ubuntu:~$ cd Desktop
endangst@ubuntu:~/Desktop$ sudo cp firefox-1.5.tar.gz /opt/
cp: cannot create regular file `/opt/firefox-1.5.tar.gz': No such file or directory
endangst@ubuntu:~/Desktop$ ls
ffsettings                           firefox-1.5.tar.gz    untitled folder
firefox                              iscabbs-2.3.8
firefox-1.5.0-0nonfree1_i386.tar.gz  iscabbs-2.3.8.tar.gz
endangst@ubuntu:~/Desktop$ sudo cp firefox-1.5.tar.gz /opt/
cp: cannot create regular file `/opt/firefox-1.5.tar.gz': No such file or directory
endangst@ubuntu:~/Desktop$ cd /opt
bash: cd: /opt: No such file or directory
endangst@ubuntu:~/Desktop$

---

### Post by shanmuha on 2006-01-01
you donot seem to have /opt directory. This is not a problem. you can create one like this:
sudo mkdir /opt

---

### Post by manicka on 2006-01-01
Also, check the howto again, you don't seem to be in the directory that you've downloaded the tarball to when copying it to /opt

---

### Post by endangst on 2006-01-01
Thanks guys.  Things are going much better than before, but now I'm hung up at

endangst@ubuntu:~/Desktop/ffsettings$ sudo cp -i --reply=no /usr/lib/mozilla-firefox/searchplugins/* /opt/firefox/searchplugins/
endangst@ubuntu:~/Desktop/ffsettings$ sudo cp -i --reply=no ~/.mozilla/firefox/*.default/search/* /opt/firefox/searchplugins/
cp: cannot stat `/home/endangst/.mozilla/firefox/*.default/search/*': No such file or directory
endangst@ubuntu:~/Desktop/ffsettings$

---

