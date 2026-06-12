---
title: "Changing charset for irssi"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by StifflerNewb on 2007-04-04
I'm currently at work, with some securityfreaks responsible for the network, and they've locked down some default ports (like 6667 or 7000 for IRC), so I use putty to ssh to my laptop at home, where I use irssi to connect to a couple of IRC servers.

Now my problem is that I'm swedish and we have åäö, which just wont display correctly in irssi. I've tried to do:
 /set recode_out_default_charset iso-8859-1

but still then wont display properly, what I've seen when googleing is that I need to change the charset for terminal, since you cant really change the charset in irssi.

Now my question(s) is:
1) Can I change the charset in irssi, and in that case how?
2) If not, how do I set the charset to iso-8859-1 that I need to use to display the letters correctly?

---

### Post by djf_jeff on 2007-04-04
Maybe try : **[SIZE=-1]/charset ISO-8859-1[/SIZE]**[SIZE=-1]


Make sure you can type those letters directly in the terminal before trying to configure irssi.[/SIZE][SIZE=-1]****[/SIZE]

---

### Post by StifflerNewb on 2007-04-04
well I figured it out by mistake. the correct term to change it is:

/set term_charset ISO-8859-1


edit:

ok, I didnt fix it. exited irssi to start it up with screen, and when I came back everything was back to "normal", this is what it looks like:
[IMG]http://img510.imageshack.us/img510/7642/irssiwn3.jpg[/IMG]

---

### Post by StifflerNewb on 2007-04-05
ï¿½
thats what I'm getting now, cant understand what the problem is!

---

