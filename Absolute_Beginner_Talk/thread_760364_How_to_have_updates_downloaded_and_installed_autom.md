---
title: "How to have updates downloaded and installed automatically?"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2008-04-20
Hello,

My father is at a point (and age) that he just doesn't really want to be hassled by computers. His windows constantly gives him all these notices which he gets crazy of; windows updates, virus software, do you want to allow this program to access the internet etc. etc.

Now I thought of making him something completely hassle-free. I know that some things might comprise safety of the user etc, but that doesn't matter. My father doesn't have many very important files. I just want him to be able to continue to use a computer to surf and email. That's all.
So, what I want is a system that doesn't ask or tell you anything. And then I mean nothing. Not the simplest thing. 

So how can I configure ubuntu that it automatically downloads updates and implements them WITHOUT asking for a password or anything?

---

### Post by joshrobinson on 2008-04-20
take a look at this

[http://www.techthrob.com/tech/updatefreq.php]("http://www.techthrob.com/tech/updatefreq.php")

---

### Post by mikeyphi on 2008-04-20
As suggested above - there are probably only 2 alternatives:

1.  Deselect all updates in Software Sources - hence no updates (yourself to update occasionally?)
2.  Select only security updates and automatic download and installation in Software Sources

I think you will find that only Security updates can be automated.

---

### Post by sayakb on 2008-04-20
Open software sources, click on Updates tab and select "Install security updates without confirmation"

---

### Post by CREEPING DEATH on 2008-04-20
You can set it up as a chron job, but I'm not totally sure how to.  Or, as suggested, just do them manually when you're visiting.

CD

---

### Post by daengbo on 2008-04-20
in a terminal, type
> sudo crontab -e
to edit the root cron script (which runs command automatically at set times. Input the following line:
> * 4 * * * apt-get update && apt-get -y upgrade
and save/exit. The command willbe run at 4am every day, and the upgrade will happen only if the update completes correctly.

You can then turn off automatic update in Software Sources.

Automatic updates are DANGEROUS. Things can go wrong. You are better off just updating security updates. Especially don't follow the above directions if you have non-distro packages and/or repositories.

---

### Post by kramer65 on 2008-04-21
> **daengbo said:**
> in a terminal, type

to edit the root cron script (which runs command automatically at set times. Input the following line:

and save/exit. The command willbe run at 4am every day, and the upgrade will happen only if the update completes correctly.

You can then turn off automatic update in Software Sources.

Automatic updates are DANGEROUS. Things can go wrong. You are better off just updating security updates. Especially don't follow the above directions if you have non-distro packages and/or repositories.

But the computer will not be turned on 24/7. WIll this also work if the computer is never turned on at 4am?
About the danger. Nothing really dangerous could happen here. In this situation I only consider physical harm to be dangerous. A total crash would only stop my dad from using it. He wouldn't really loose anything. He just wants to surf the internet and use his (online) mail.


> **LinuxIsInnovation said:**
> Open software sources, click on Updates tab and select "Install security updates without confirmation"

Thanks for this. But would this mean that my dad will never be asked for any update anymore?

---

### Post by Hairy_Palms on 2008-04-21
if you want to remove the popup from the tray, then just open synaptic and uninstall update-notifier and update-notifier-common

---

### Post by kramer65 on 2008-04-21
So it is in no way possible to simply accept all updates which the system tray thingy would give you? That's what I do myself anyway as well. I normally don't really have a clue what is updated but just accept it.

I just trust the updates and don't have the technical knowledge the differentiate good from bad updates. Since I can't even do that I don't expect my father to know anything of that. He is normally happy if he can simply startup the browser. He doesn't use the computer for music, movies, or anything else than email and internet.

Nobody can tell me how I can accept all updates by default?

---

### Post by hums07 on 2008-04-21
In your situation, I prefer no update at all. No update no hassle until a new Ubuntu version come out and fresh install the next version. Simply follow mikeyphi's post above ([http://ubuntuforums.org/showpost.php?p=4751381&postcount=3](http://ubuntuforums.org/showpost.php?p=4751381&postcount=3))

---

### Post by kramer65 on 2008-04-21
Ok thank you.I will do that then. I will automate only security updates. 

When I am at my fathers place though. How do I manually update everything?

---

### Post by hums07 on 2008-04-21
> **kramer65 said:**
>  How do I manually update everything?

Alt-F2. Type "update-manager".
Also there is a menu to the application.

---

### Post by kramer65 on 2008-04-21
Thank you!

Now I know what to make for my father. I will give him a clean ubuntu install with microsoft office installed with crossover office.

I probably give him a desktop that looks something like this; [http://ctolpin.googlepages.com/momfriendly.png](http://ctolpin.googlepages.com/momfriendly.png)
One big icon for the internet. I might even set the icon to the internet explorer icon. He wouldn't know whats the difference between FF and IE. And and icon for the word processor.

Haha, I started with ubuntu about a year ago and am happy with it. Friends called me crazy but I've converted 2 friends already and now I'll convert my dad. Well, I probably don't even tell him that it is not windows. He just doesn't want to be bothered.. :-)

---

### Post by 3rdalbum on 2008-04-21
Make sure you set up ssh with "AllowUsers" set to only your account, and have a double-strong password on that account (if there are two passwords that you use in daily life, put those together).

Don't forget, if your father has a modem with a firewall in it (most do), then you should forward port 22 on that firewall.

The net effect being that you'll be able to remotely administer the system. If necessary, you could run sudo apt-get dist-upgrade remotely. At the very least, if he complains that something isn't working properly or that he needs a new program, you can do these things for him.

---

### Post by kramer65 on 2008-04-21
Thank you for those tips.

What is allowusers? That only him can enter?

About the remotely administering. I would love to be able to do that. I've never worked with it though. I would first like to set that up on my own system to check it out. I'm behind a router AND a hub, so I wouldn't know how to do that. Is there some kind of how-to which I can follow somewhere to set it up?

---

