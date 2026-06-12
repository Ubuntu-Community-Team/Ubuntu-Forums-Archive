---
title: "New to linux... Need to update from 5.04 to 5.10"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by Tummas on 2005-12-05
I just got a ubuntu install cd at school, but when i installed it i found out that there was a newer version out. To update from 5.04 to 5.10 do i have to download the entire install cd (about 600MB) ?:???:

---

### Post by IdolizingStewie on 2005-12-05
If you don't want to download the new Ubuntu, you can go to the terminal and type these commands: ```
sudo apt-get update
sudo apt-get dist-upgrade
```That should upgrade you to 5.10. You can probably also do the same thing in Synaptic if you prefer GUIs, but I don't know how.

---

### Post by Galoot on 2005-12-05
Keep in mind that if what you have works, you don't *have* to upgrade. Why fix what ain't broke? The maintainers will continue to support for another year what you're running, so security isn't really an issue.

Still, if you'd rather, and you're not into downloading the entire 600MB, you could always get the new version on CD [shipped to you for free]("http://shipit.ubuntu.com/").

---

### Post by Tummas on 2005-12-05
I tryed typing in those commands but all i got was, "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."! :???:

---

### Post by Tummas on 2005-12-05
ok, so if i have the new cd, can i just use it to update with or do i have to format?

---

### Post by SavageBeginner on 2005-12-05
To upgrade from 5.04 to 5.10 you need to change all occurrences of 'hoary' in /etc/apt/sources.list to 'breezy'

```
sudo gedit /etc/apt/sources.list
```
Find every 'hoary' and change to 'breezy'.  Save and Exit.

Then:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by IdolizingStewie on 2005-12-05
D'oh. That'll teach me to give instructions I've never actually used.

---

### Post by timfrost on 2005-12-05
[QUOTE=Tummas]I just got a ubuntu install cd at school, but when i installed it i found out that there was a newer version out. To update from 5.04 to 5.10 do i have to download the entire install cd (about 600MB) ?:???:[/QUOTE]

You don't have to download the CD 

However, you *will* have to download all of the packages from breezy which are upgrades of the existing packages in your  hoary installation.

If you have some way of getting a breezy CD without downloading it yourself, then that will give you all the software from the "main" repository.  You will still have to download  the security updates (which include a new kernel), and any updates from universe or multiverse.

Remember to update your sources.list so that you use the breezy repositories instead of hoary/warty


Tim

---

### Post by AndyCooll on 2005-12-05
[QUOTE=Tummas]I tryed typing in those commands but all i got was, "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."! :???:[/QUOTE]

I think you might first need to change your souces.list.

# gedit /etc/apt/sources.list

Edit that file by changing each occasion of the word hoary to breezy. Save that. Then repeat the instructions mentioned above.

:cool:

---

### Post by frodon on 2005-12-05
All the instructions are here : [https://wiki.ubuntu.com/BreezyUpgradeNotes?](https://wiki.ubuntu.com/BreezyUpgradeNotes?)

---

### Post by jrfoleyjr on 2007-07-05
I am currently running5.10

How can I upgrade to a newer package? I am a total linux noob, making a move from windoze and installed 5.10 to discover that there are much newer versions available. From the pulldown menu the update manager tells me I am up to date.  HELP!

---

### Post by Feba on 2007-07-05
Err.... At that point, it's probably better to get a 7.04 CD and reinstall. You'd probably run into so many problems trying to update...

---

