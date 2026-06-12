---
title: "Some Problems"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by infin?ty on 2006-06-21
Hi all, i am new to ubuntu and linux, i am getting following problems
I use Ubuntu 'breezy badger'.

1.) I am trying to install this software called gnuchess but after giving the make command its giving these errors

input.c:95:error: static declaration of 'input_thread' follows non_static declaration.

common.h:725:error: previous declarationof 'input_thread' was here.

wats the problem here is it in the source files, or is it because i am doin something wrong.


2.) While installing xmms player i got these errors, this was while running ./configure

The glib_config script installed by GLIB could not be found.
if GLIB was installed in PREFIX make sure PREFIX/bin is in your path, or set GLIB_CONFIG environment variable
to the full path of glib_config.

configure:error:GLIB>=1.2.2 not installed please install first.

How do i change he environment variable.

 One more thing how do i install GTK on UBUNTU.

---

### Post by bikeboy on 2006-06-21
I can help you with some of the problems. Installing most software is easy, gnuchess and xmms are in the repositories of software to choose from.

Simply type:```
sudo aptitude install gnuchess xmms
```
You could use apt-get instead of aptitude but it's not as good when removing software.

If you want more software to choose from check out this link for how to add the Universe and Multiverse repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu/Breezy](https://help.ubuntu.com/community/Repositories/Ubuntu/Breezy)

---

### Post by infin?ty on 2006-06-21
But I reckon i would be needing an internet connection for that. But another problem with me is that i dont know how to configure my Ubuntu to internet, right now i access internet frm windows. I have an ADSL coneection, so could u help me with that first.  Thanks.

---

### Post by Nikusan on 2006-06-21
[QUOTE=infin?ty]But I reckon i would be needing an internet connection for that. But another problem with me is that i dont know how to configure my Ubuntu to internet, right now i access internet frm windows. I have an ADSL coneection, so could u help me with that first.  Thanks.[/QUOTE]

How do you connect to the ADSL? USB? Ethernet?

---

### Post by MaximB on 2006-06-21
I've asked the same question about adsl
and I recived an answer
go to the console/terminal and enter the command :
sudo pppoeconf
after that enter your password
and you will get to the adsl setup - there you'll enter your adsl provider , your username and password

I used ubuntu 6.06....not the 5.10
but I think it would work just fine...

---

