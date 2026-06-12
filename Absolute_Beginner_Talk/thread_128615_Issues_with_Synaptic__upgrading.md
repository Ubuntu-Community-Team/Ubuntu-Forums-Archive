---
title: "Issues with Synaptic / upgrading"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by xx75 on 2006-02-11
Hi all,
Absolute beginner here in need of help from someone higher up the intelligence chain....

It recently came to my attention that the regular updates that appear on my desktop do not show up anymore. When I do an apt-get update/upgrade I get this -
[I][COLOR="Blue"]xx75@Machine:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
[/COLOR][/I]
I can't add repositories to my Synaptic either, well I can, but they delete as soon as I click OK.
When I load Synaptic from terminal I get this -
[I][COLOR="Blue"]xx75@Machine:~$ sudo synaptic

(synaptic:11748): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:11748): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
[/COLOR][/I]

I have also just noticed that not all the repositories in my apt-get sources list are showing when I do an apt-get update

I am having trouble finding a solution for this one.

Thanks in advance.
xx75

---

### Post by o_fortuna on 2006-02-11
[QUOTE=xx75]Hi all,
Absolute beginner here in need of help from someone higher up the intelligence chain....

It recently came to my attention that the regular updates that appear on my desktop do not show up anymore. When I do an apt-get update/upgrade I get this -
[I][COLOR="Blue"]xx75@Machine:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
[/COLOR][/I]
I can't add repositories to my Synaptic either, well I can, but they delete as soon as I click OK.
When I load Synaptic from terminal I get this -
[I][COLOR="Blue"]xx75@Machine:~$ sudo synaptic

(synaptic:11748): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:11748): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
[/COLOR][/I]

I have also just noticed that not all the repositories in my apt-get sources list are showing when I do an apt-get update

I am having trouble finding a solution for this one.

Thanks in advance.
xx75[/QUOTE]
First: When running Synaptic from the terminal, use gksudo, NOT sudo. That's just a general rule (for GUI apps) which probably won't fix anything, since I'm getting the same errors and haven't had problems. About the packages being held back, use dist-upgrade rather than upgrade. Finally, the best way to change repositories is:
```
sudo gedit /etc/apt/sources.list
```
I've always found the GUI to be annoying and painful.

---

### Post by xx75 on 2006-02-11
Hi o_fortuna

Thanks for your reply

Apologies, I did actually use gksudo initially but forgot to do so when I wanted to copy and paste the message. It gave me very similar results so I didn't look twice. here is what I got using gksudo synaptic -

[COLOR="Blue"][I]xx75@Machine:~$ gksudo synaptic

(synaptic:13311): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:13311): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed[/I][/COLOR]

[B]sudo gedit /etc/apt/sources.list
[/B]
I had already done this but I just noticed that most of my repositories had a ## in front of them, I just removed these now and problem's gone.

I am doing the apt-get dist-upgrade now

Thanks for your time
xx75

---

