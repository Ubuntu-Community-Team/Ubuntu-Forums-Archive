---
title: "how to find your ip address from the system"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by crunchystrike on 2006-09-23
ok, i remember in windows, u go to /run/cmd/ipconfig and it tells you ur ip address and the routers address, i need to know how to find my ip in Ubuntu so i can set my NAT properly for Azureus,

---

### Post by YeahBuntu on 2006-09-23
In terminal it is Ifconfig I believe.

---

### Post by chrisfay on 2006-09-23
Ifconfig != ifconfig

---

### Post by sarum on 2006-09-23
joe@Joes-pc:~$ Ifconfig != ifconfig
bash: Ifconfig: command not found
joe@Joes-pc:~$
Thats what I get; any suggestions.
Sarum

---

### Post by twide on 2006-09-23
just type in > ifconfig

---

### Post by sarum on 2006-09-23
Sorry sorry sorry. I see my mistake.
 _Ifconfig_ is the same as _ifconfig_
I'll shut up now and get back in my box.
Sarum.

---

### Post by chrisfay on 2006-09-23
> Sorry sorry sorry. I see my mistake.
Ifconfig is the same as ifconfig
I'll shut up now and get back in my box.

Ifconfig is NOT the same as ifconfig. That was my point....lol

---

### Post by gezzabob on 2006-09-23
Try Applications > Accessories > Terminal.

And then type in ifconfig to get your ip address etc.

As usual man ifconfig will give you the help page on ifconfig and its various setting.

But as you mention you wanting to setup Azureus and NAT firewall settings etc.  It may prove fruitful to use firestarter to edit your linux firewall settings.

If you have not already got firestarter installed it should be as simple as goto Applications > Add/Remove Applications, search for firestarter tick the show unsupported applications tick box, select firestarter and install (put in your password when prompted).  If firestarter doesnt show up in the add/remove Applications you may need to setup the correct repositories (cannot remember now it was a while when I set up firestarter if that is the case post the question and somebody should help if not I will back track and look into it for you).

Once firestarter is installed follow the wizard to set it up, should be able to start it from Aplications > Internet > Firestarter.

Firestarter is a graphical front end for the linux in-build firewall - iptables.

To summerise, Linux ip configure command - ifconfig is like Microsoft ip address configure command - ipconfig.

Firestarter is a GUI (Graphical User Interface) for iptables that controls the in-build firewall in Linux(the firewall is on and running by default in Linux.. Firestarter just gives you a GUI to configure and monitor the firewall).

Of course I am no guru, but that should at least get you going on your quest to get Azurues up and running.

:D 

Gezzabob.

---

### Post by p.i.m.p on 2006-09-23
or u cud type ip addr

if u have a dsl connection, ```
ip addr|grep ppp
``` should do it

---

### Post by wildseven on 2006-09-23
> **chrisfay said:**
> Ifconfig is NOT the same as ifconfig. That was my point....lol

heh he was being sneaky! lol

in programming != is the symbol for not equal to heh~

sooo infact
Ifconfig != ifconfig
ifconfig does not equal ifconfig

^^

---

### Post by MWAAAHAAA on 2006-09-23
> **wildseven said:**
> heh he was being sneaky! lol

Ifconfig != ifconfig
ifconfig does not equal ifconfig

^^

No you got it wrong too,

Ifconfig != ifconfig
Ifconfig does not equal ifconfig

People, please take a moment when writing in the newbee forum, as this can be *very* confusing for newcomers.

crunchystrike: In linux file names are case-sensitive, i.e. it matters whether you use capitals or just small letters.

---

### Post by chrisfay on 2006-09-23
> No you got it wrong too,

Ifconfig != ifconfig
Ifconfig does not equal ifconfig

lol.....finally

Next time I'll be less enigmatic....

---

### Post by sarum on 2006-09-23
Thanks Wildseven, I feel better now.
.........Sarum

---

