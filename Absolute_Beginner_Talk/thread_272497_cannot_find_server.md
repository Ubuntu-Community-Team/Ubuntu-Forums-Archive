---
title: "cannot find server"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by chiasc on 2006-10-06
i have installed 6.06 ubuntu.the modem was autodetect at /dev/ttys0.the isp was connected,but when firefox was fired,
popup message "cannot find server" shown([www.google.com),but](www.google.com),but) i
am sure the modem connection was on.Please help me!!.

---

### Post by madmetal on 2006-10-06
look at system>>system management>>network
give sudo password and check the dns settings.
set the right dns servers..
i think this will fix it..

---

### Post by chiasc on 2006-10-08
i had tried naming the dns and disable ipv6 through firefox(about:config),but still couldn't log on [www.google.com](www.google.com).
the modem is connection but in idle.
i'm suck,please help.

---

### Post by jlsheehan on 2006-10-08
Hi there,

It is really hard to help someone with only small amounts of information like this.

It sounds like you are using a dial-up connection, have you entered all your settings in the System -> Administration -> Networking config tool?

If you look in the Ubuntu Documentation there is a section on connecting to the internet, this might also give you some help.  It is in System -> Help -> System Documentation.  Section 4.3.5 is on modems and 3.4.1 is on connecting to the internet.

Jeff

---

