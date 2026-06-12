---
title: "what is debian-apps-net?"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by wog on 2006-06-09
I'm not sure where to put this.

I have a problem I don't know how to solve that I think I need to before upgrading to Dapper. It's a warning I get every so often, something about debian-apps-net, which I can't seem to find in the forums, synaptic, the man pages or in updatedb. 

Any pointers?

---

### Post by brentoboy on 2006-06-09
you say you have a problem with it, what are the symptoms?

BTW, it sounds to me like a repository that has been added to your sources.list that doesnt exist anymore (if it ever did).

if that is the case, it is as easy as 
sudo gedit /etc/apt/souces.list
and removing the entry for debian-apps-net

but I dont think it will hurt you either way just update all your sources in the sources list file to be dapper instead of breezy, and then
sudo apt-get update
sudo apt-get dist-upgrade

it will ignore repos it cant connect to anyway.

---

### Post by wog on 2006-06-09
Do I need to worry about those GPG keys, or do they matter when doing dist-upgrade?

---

### Post by brentoboy on 2006-06-09
unsure.

without gpg keys, you wont know for sure if the packages were indeed signed by the folks at ubuntu before they get installed.

I dont think this is a big deal, it will ask you if you want to install package(s) xyz even though you cant confirm its publisher.

it will work with or without the keys, but you will have to say "yes" a few more times.

techinically, it is best to get the keys in correctly, (I dont think they changed from breezy to dapper, but I cant confirm that)

---

### Post by wog on 2006-06-09
The original error message was GPG Error: No Pubkey, and a string of hexcode, but I commented out the cipherfunk line to deal with it and it hasn't bothered me since.

Did something change with the cipherfunk site?

---

### Post by wog on 2006-06-10
Assured that Dapper would install without difficulty, I installed it. The install died halfway through, and after much fussing with it, I did a clean install, wiping the entire hard drive.

Problem solved.

All good command lines, I will keep them in mind for when I attempt to take a slice out of the main partition for my ~/home directory. :)

Sorry I'm so dead-pan, I think I'm still in shock. I am grateful.

---

