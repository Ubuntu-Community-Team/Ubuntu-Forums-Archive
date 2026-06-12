---
title: "Firewall, Anti virus, Spyware"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by xander848 on 2006-07-04
Ok im pretty new to linux (about 2 weeks) and I was wondering if I need to install a firewall, antivirus, or spyware program. I know linux is more sucure and all but do I need them?

If so any suggestions would be great.

---

### Post by Simian on 2006-07-04
firewall is built into the kernel, iptables, but you might want to install the gui front end, firestarter to make life easier. As for spyware and antivirus software, most people don't bother as there is no risk of infection (yet).

---

### Post by MaximB on 2006-07-04
I don't see any way a virus could harm you ubuntu as by default you are NOT a super user and to do administrative tasks you need to enter your password every 15 minutes
but in other linux distrebutions - you are always logged as a su.

---

### Post by woedend on 2006-07-04
iptables is an empty shell.  You need a ruleset, which firestarter provides.

---

### Post by Kilz on 2006-07-04
[quote=xander848]Ok im pretty new to linux (about 2 weeks) and I was wondering if I need to install a firewall, antivirus, or spyware program. I know linux is more sucure and all but do I need them?

If so any suggestions would be great.[/quote]
The odds are real low you could be infected. You dont need anti spyware or antivirus programs. Becasue even if something is picked up. Its only going to effect the user account. You could delet the user account and add another without much trouble.
But that isnt an excuse to avoid bad pratices. Stick to software from Synaptic, dont download things from iffy sites. You can still install something that is bad.

[QUOTE=MAXDDARK]I don't see any way a virus could harm you ubuntu as by default you are NOT a super user and to do administrative tasks you need to enter your password every 15 minutes
but in other linux distrebutions - you are always logged as a su.[/QUOTE]
Most Linux distro's preach against running as root. Linspire used to have users run as root but doesn't any more. The only OS that its common to run as root in, is Windows. Ubuntu takes it a step farther and gets rid of the root login.

---

### Post by MaximB on 2006-07-04
yes...so how possible a virus can harm ubuntu ? (except maybe harm your user).

---

### Post by ajgreeny on 2006-07-04
Because I dual boot with windows, I installed clamav virus scanner and use it about once a month, but that is largely paranoia, as there are no viruses in the wild for linux yet.  However I do send files to other Windows users some times so it makes sense to know I'm squeaky clean.
I did install Firestarter, but it didn't make any difference when I did a scan online to how things were before it was installed so again I feel that is just paranoia.
This, I feel, is the biggest advantage of using Ubuntu; no worries about any of the things that I spent a lot of time considering when using Windows; no spyware, no trojans, no browser hijacking, no viruses.
Great, isn't it?

---

### Post by Simian on 2006-07-04
Some might say that you should install antivirus software in case you are sent an email containing a virus designed for a windows PC, it wouldn't infect your machine. But if you were to forward that email (possibly to a windows PC), it will be caught. And you will have the satisfaction knowing that you have done your bit to help prevent the spread of infection.

---

### Post by lamego on 2006-07-04
It is true that is very unlikely to see virus/spyware for linux so widespread as you see for windows, but it is not safe to think that just because you are not superuser it will not hurt you.
All the files that you really care about (data files) are accessible by you and could be damaged by the malware.
Anyway this is not really something you need to worry about right now.

---

### Post by MiKuS on 2006-07-04
in the end, unless you open something and don't know ultimatly where it's from then you pose a risk of hurting your operating system, same goes for windows.

don't open cracks, keygens and software of that context and your computer should be fine.

as for adware well....i'm sure if a company really wanted to infect a linux box they might find it more dificult then infecting a windows box, but not impossible.

---

### Post by FredB on 2006-07-04
[QUOTE=woedend]iptables is an empty shell.  You need a ruleset, which firestarter provides.[/QUOTE]

Empty shell ?! So why my computer safe with [Shields up]("https://www.grc.com/x/ne.dll?bh0bkyd2") test ? Or in [PCFlank]("http://www.pcflank.com/") one ?

Why ?!

---

### Post by woedend on 2006-07-04
because you have no ports listening/open by default.
read up on iptables and in particular netfilter.

---

