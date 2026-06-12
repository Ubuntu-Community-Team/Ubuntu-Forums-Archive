---
title: "rm -rf /"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2006-02-24
I get bored some times so last night I ran "rm -rf /" (all my important docs are on hda3 /home so no worries) on my server install.  I like to break stuff and try to fix it.  So i just reformatted a server install (it only takes about 15 minutes) on hda1.  So my question is how do I make an alias so I or anyone else can't run "rm-rf /".  Thanks for the help.

---

### Post by mostwanted on 2006-02-24
/ is usually (well, always) owned by root which means you have to be super-user to change it. I don't understand how you could do a rm -rf / without prefixing it with sudo...?

However, on any normal install / will be the root partition and you will require root privileges to write to it, thus rm -rf / isn't possible for normal users.

---

### Post by echo $USER on 2006-02-24
I'm sorry, I left that part out.  I used "sudo rm -rf /" then I would run something like "nmap 127.0.0.1" "/usr/bin directory not found" So I know it worked.  What I want to know is how do I make an alias so no one can run "sudo rm -rf /". Thanks.

---

### Post by mostwanted on 2006-02-24
Unless you tell them the super-user password, they won't, that's the idea of the sudo command you know ;) It doesn't just magically grant you root privileges, you still need to type the password.

---

### Post by echo $USER on 2006-02-24
I guess I'll just disable the root account once I get my server the way I want it.  

where is this going to happen [SIZE="4"]Roskilde Festival[/SIZE] I;ve seen R. Waters once in new orleans about four years ago, but he didn't do any floyd tracks.  I'd love to see him play dark side.

---

### Post by mostwanted on 2006-02-24
There's no root account in Ubuntu, only a super-user password (which is the password of the first user added).

The Roskilde Festival is in Denmark. It's the second-biggest festival in Europe, very popular with Scandinavians obviously, but also Germans, Dutch and other relatively Northern people. Not Britons, but they have Glastonbury so that's probably why (+ Brits rarely care for much else than British and American music ;) ).

---

### Post by echo $USER on 2006-02-24
Is it a two-three day show?  I'd love to go to a festival in Europe.  I tried to check out the website, but my comany's stupid firewall won't let me access it.  And my squid proxy server is down due to my actions last night so I can't use that to access it either.  I'll definatly check it out once i get home this evening.

---

### Post by mostwanted on 2006-02-25
I think the main music part is about 3-4 days, but usually people come some days before it starts and some stay a day or two afterwards (lots of amateur bands playing + partying going on).

---

### Post by aysiu on 2006-02-25
[QUOTE=echo $USER]I get bored some times so last night I ran "rm -rf /" (all my important docs are on hda3 /home so no worries) on my server install.[/QUOTE] If /dev/hda3 is actually mounted at /home when you run ```
sudo rm -rf /
``` then everything there will be deleted as well.

---

