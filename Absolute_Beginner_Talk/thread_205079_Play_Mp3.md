---
title: "Play Mp3"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by hardfire_avk on 2006-06-27
How do i play Mp3 files in ubuntu.

I get this if i try to play it in totem

> There were no decoders found to handle the stream, you might need to install the corresponding plugins

---

### Post by siccness on 2006-06-27
I guess the easiest way for you to do this is by installing the codecs, but making this an easier job for you is to download EasyUbuntu.

Link: 
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

---

### Post by blackjack6.21.91 on 2006-06-27
Ubuntu is not legally allowed to give you some codecs on default install. You can                get these using [bumps.]("http://www.ubuntuforums.org/showthread.php?t=181248")

---

### Post by az on 2006-06-27
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by hardfire_avk on 2006-06-27
Easy ubuntu gave me this..

```


avinash@avinash:~$ wget http://easyubuntu.freecontrib.org/files/easyubuntu-3.02.tar.gz
--20:44:36--  http://easyubuntu.freecontrib.org/files/easyubuntu-3.02.tar.gz
           => `easyubuntu-3.02.tar.gz'
Resolving easyubuntu.freecontrib.org... 213.246.58.132
Connecting to easyubuntu.freecontrib.org|213.246.58.132|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 107,354 (105K) [application/x-tar]

100%[====================================>] 107,354        3.09K/s    ETA 00:00

20:45:19 (2.73 KB/s) - `easyubuntu-3.02.tar.gz' saved [107354/107354]

avinash@avinash:~$ tar -zxf easyubuntu-3.02.tar.gz
avinash@avinash:~$ cd easyubuntu
avinash@avinash:~/easyubuntu$ sudo python easyubuntu.in
Password:
System sanity check: PASSED!
['/usr/sbin/synaptic', '--hide-main-window', '--non-interactive', '-o=dir::etc=./conf', '-o=dir::etc::sourcelist=sources.list']
In update ['/usr/sbin/synaptic', '--hide-main-window', '--non-interactive', '-o=dir::etc=./conf', '-o=dir::etc::sourcelist=sources.list', '--update-at-startup']
(synaptic:8155): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:8155): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
In Install ['/usr/sbin/synaptic', '--hide-main-window', '--non-interactive', '-o=dir::etc=./conf', '-o=dir::etc::sourcelist=sources.list', '--set-selections']

(synaptic:8158): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:8158): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Traceback (most recent call last):
  File "/home/avinash/easyubuntu/EasyUbuntu/gtkfrontend.py", line 159, in on_ok_button_clicked
    logger = gtkLogger(self.packageslist, self.configslist, self.confdir)
  File "/home/avinash/easyubuntu/EasyUbuntu/gtkprocess.py", line 90, in __init__    vbox.pack_start(button, FALSE, FALSE)
NameError: global name 'FALSE' is not defined


```

---

### Post by hardfire_avk on 2006-06-27
[QUOTE=azz][https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) page has this.

> #

Ubuntu 5.10 (Breezy Badger)

    *

      Install the package gstreamer0.8-mad.



[/QUOTE]

When i started the synaptic package manager. I didn't get any package called as gstreamer0.8-mad.. There is 

gstreamer0.8-alsa
gstreamer0.8-audiofile
gstreamer0.8-cdparanoia
gstreamer0.8-dv
gstreamer0.8-dvd
and lots more but not gstreamer0.8-mad.

---

### Post by classem2003 on 2006-06-27
[QUOTE=hardfire_avk]How do i play Mp3 files in ubuntu.

I get this if i try to play it in totem[/QUOTE]
To listen to music  I use xmms. It looks like winamp. To do it in the easy way, go to synaptic then settings>preferences  then check the box " consider recomended packages as depencies" . Then install xmms and all the libraries and extra packages that you need will be installed.

---

### Post by hardfire_avk on 2006-06-27
[QUOTE=classem2003]To listen to music  I use xmms. It looks like winamp. To do it in the easy way, go to synaptic then settings>preferences  then check the box " consider recomended packages as depencies" . Then install xmms and all the libraries and extra packages that you need will be installed.[/QUOTE]

I don't have a package called as xmms.

---

### Post by lapsey on 2006-06-28
i appears you dont have the multiverse and other unofficial package repositories added to synaptic.
But, since easyubuntu didnt work out for you, you may find that automatix will work. It did for me. [http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

And if that doesnt work you can add the repositories and the codecs yourself: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

edit: beatn. reinforcement thru repetition i guss :)

---

### Post by HereInOz on 2006-06-28
To install gstreamer0.8-mad you must have first enabled the Universe and Multiverse repositories.  There are instructions on how to do this in the Restricted formats page.  Do that, and gstreamer0.8-mad will then be available through synaptic.

Hope this helps,

Alan

---

