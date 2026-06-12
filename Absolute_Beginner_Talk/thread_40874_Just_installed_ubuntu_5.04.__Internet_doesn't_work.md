---
title: "Just installed ubuntu 5.04.  Internet doesn't work"
date: 2005-06-10
forum: Absolute Beginner Talk
---

### Post by dbzsongoku on 2005-06-10
Hi,
I am a windows user that wants to switch to linux.  I installed it and everything seems to be working fine except I can't connect to the internet.  The computer that I have is a dell 700m laptop and I am connect this to a router which is connected to a cable modem.  This is the error message that I get when I log in.

Could not look up internet address for ubuntu. This will prevent GNOME from operating correctly. It may be possible to correct the problem by adding ubuntu to the file /etc/hosts

Can someone please help me fix this problem?
thanks

---

### Post by desdinova on 2005-06-10
[QUOTE=dbzsongoku]Hi,
I am a windows user that wants to switch to linux.  I installed it and everything seems to be working fine except I can't connect to the internet.  The computer that I have is a dell 700m laptop and I am connect this to a router which is connected to a cable modem.  This is the error message that I get when I log in.

Could not look up internet address for ubuntu. This will prevent GNOME from operating correctly. It may be possible to correct the problem by adding ubuntu to the file /etc/hosts

Can someone please help me fix this problem?
thanks[/QUOTE]
 sudo gedit /etc/hosts

add an entry

ip.address.of.machine                                      ubuntu

replacing ip.address.of.machine with the ip address the router gives you

---

### Post by dbzsongoku on 2005-06-10
Thanks for the reply.  I just tried that and it got rid of the message, but I still can't go on the internet.

---

### Post by dbzsongoku on 2005-06-10
[QUOTE=dbzsongoku]Thanks for the reply.  I just tried that and it got rid of the message, but I still can't go on the internet.[/QUOTE]
 I've tried connecting it directly to the cable modem and it still doesn't work.

---

### Post by dbzsongoku on 2005-06-10
nvm.  I got it working.  Now I need help setting up my wireless internet so that I can go online anywhere in the house.

---

### Post by somuchfortheafter on 2005-06-10
check the forums for ndiswrapper that should help you if your card automatically doesnt work...

---

### Post by dbzsongoku on 2005-06-11
[QUOTE=somuchfortheafter]check the forums for ndiswrapper that should help you if your card automatically doesnt work...[/QUOTE]
 I am gogin to reinstall the OS again cause I just screwed something up when I was trying to set the resolution to 1280x800 and now it doesn't boot into the gui anymore.  I'll check out that ndiswrapper thing later.  Thanks

---

### Post by illusionaz on 2005-06-28
Just wanted to thank you, this seems to have solved my networking issues. For example I couldn't update ubuntu or open "Networking" from the system menu. 

For other people's reference (I am a newb so I think it may be helpful), just add the line below the top 2 lines. 

New linux user,

Adam Paoli
Co-Owner
[http://www.gamer-talk.net](http://www.gamer-talk.net)

---

