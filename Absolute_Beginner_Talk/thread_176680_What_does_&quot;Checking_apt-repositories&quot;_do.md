---
title: "What does &quot;Checking apt-repositories&quot; do at the end of a fresh Breezy install?"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by harisund on 2006-05-15
I think anybody who has installed Breezy would have observed this. Just after you finish installing everything and are about to reboot your computer to unpack the software, the status message "Checking apt-repositories" is shown. 

My question, what does it do and what is it's point? 

As a regular poster on these forums and a regular participant on the IRC channels helping out people, one of the things I observe is that inspite of the fact that universe and multiverse are not *official* and *not directly supported* people will definitely still include them in the repositories listing. 

The other thing, by default the repositoris listing includes the CD as well and that is in fact the first repository. 

Now, here is my idea and suggestion, something I would really like implemented

When the installation is finished, a message should be shown informing the user about repositories, and asking the user whether he wants the repositories to be added (with the default being yes. -- and a message like "If you don't know what this means, the answer is probably yes").

And the CD should be removed from the listing if the installer has detected a DHCP connection that is configured correctly (and if possible an *apt-get update* must be run silently too)

This way, the problems of a ton of users can be removed, since I see that most users are pointed towards information regarding addition of repositories and updating anyway.

---

### Post by kencoe on 2006-05-16
[QUOTE=harisund]My question, what does it do and what is it's point? [/quote]
Someone else may correct me on this, but I believe the best way to explain is that it is checking what you have installed, and what is available, to form the local list on your computer of updates, apps, and installed software for Synaptic and the Update manager.

[QUOTE=harisund]When the installation is finished, a message should be shown informing the user about repositories, and asking the user whether he wants the repositories to be added (with the default being yes. -- and a message like "If you don't know what this means, the answer is probably yes").

And the CD should be removed from the listing if the installer has detected a DHCP connection that is configured correctly (and if possible an *apt-get update* must be run silently too)

This way, the problems of a ton of users can be removed, since I see that most users are pointed towards information regarding addition of repositories and updating anyway.[/QUOTE]

I would propose that if they don't know yet what the repository list is, then they are more likely to get into an unsupported problem or an issue above their head from universe and multiverse. That is why they add it by hand.

The standard list of repositories (and the CD in case what you are trying to install or fix is the broken package keeping you from accessing the internet) is the list that is stable, has been fully tested, and is supported. If someone stays to this list, their chances of system breakage or inability of finding an answer are exponentially lower. 

It also helps us US users with the STUPID digital formats laws, but you don't want me to go into that...

---

