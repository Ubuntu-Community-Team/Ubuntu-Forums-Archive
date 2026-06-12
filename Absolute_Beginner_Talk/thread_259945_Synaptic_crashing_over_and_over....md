---
title: "Synaptic crashing over and over..."
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by BasNL on 2006-09-18
Hey guys, I'm new here. New to linux and ubuntu too as a matter of fact. Ik decided to try ubunto after reading an article about it on a Dutch forum. Installed like a breeze, works like a charm. Just one tiny litte glitch. 

I can't install any programs that aren't on the standard synaptic list. To be more specific... I wanted to install vlc media player. As the videolan website states I opened up synaptic package manager and went to settings --> repositories. Now this is where it starts driving me insane.

Whenever I try to open up the repositories I get this pop up screen:

**Repositories changed**

*The repository information has changed. You have to click on the "Reload" button for your changes to take effect*

So I reloaded and tried opening the repostories again. I think something got stuck there. Does anybody here have any kind of idea how to fix this?

---

### Post by Najand on 2006-09-18
Hmm, use the manual command at the terminal:
(Terminal: Applications -> Accessories -> Terminal)
And the type :
```

sudo aptitude update && sudo aptitude upgrade

```
 and see if it is successful or not.

---

### Post by Obor on 2006-09-18
I'm just guessing but maybe there is something funny in your repo list. Try opening the terminal and type
```
sudo apt-get update
```

and see what kind of error messages, if any, you'll get. Post it here and maybe it will make sence to someone.

Edit: too late :D

---

### Post by BasNL on 2006-09-18
> **Obor said:**
> I'm just guessing but maybe there is something funny in your repo list. Try opening the terminal and type
```
sudo apt-get update
```

and see what kind of error messages, if any, you'll get. Post it here and maybe it will make sence to someone.

Edit: too late :D

This is what I got. 
```
sudo apt-get update
bas@bas-desktop:~$ sudo apt-get update
Password:
Ophalen:1 http://nl.archive.ubuntu.com dapper Release.gpg [189B]
Ophalen:2 http://nl.archive.ubuntu.com dapper-updates Release.gpg [189B]
Ophalen:3 http://security.ubuntu.com dapper-security Release.gpg [189B]
Geraakt http://nl.archive.ubuntu.com dapper Release
Ophalen:4 http://security.ubuntu.com dapper-security Release [30,9kB]
Geraakt http://nl.archive.ubuntu.com dapper-updates Release
Geraakt http://nl.archive.ubuntu.com dapper/main Packages
Geraakt http://nl.archive.ubuntu.com dapper/restricted Packages
Geraakt http://nl.archive.ubuntu.com dapper/main Sources
Geraakt http://nl.archive.ubuntu.com dapper/restricted Sources
Geraakt http://nl.archive.ubuntu.com dapper-updates/main Packages
Geraakt http://nl.archive.ubuntu.com dapper-updates/restricted Packages
Geraakt http://nl.archive.ubuntu.com dapper-updates/main Sources
Geraakt http://nl.archive.ubuntu.com dapper-updates/restricted Sources
Ophalen:5 http://security.ubuntu.com dapper-security/main Packages [49,1kB]
Ophalen:6 http://security.ubuntu.com dapper-security/restricted Packages [4269B]Ophalen:7 http://security.ubuntu.com dapper-security/main Sources [12,1kB]
Ophalen:8 http://security.ubuntu.com dapper-security/restricted Sources [964B]
97,6kB opgehaald in 2s (46,0kB/s)
Pakketlijsten worden ingelezen... Klaar

``` *sorry for the Dutch language...*

Seems ok doesn't it? I still can't get into the repositories in synaptic afterwards however.

---

### Post by Najand on 2006-09-18
I don't know any dutch but I assume klaar means ready, right?
Then there is no problem I think.... Try Synaptic and see if you receive errors again or not.

---

### Post by BasNL on 2006-09-18
When I hit the reload button I get a pop up stating that it is downloading package information. 22 files to be exact. When I hit reload again after that, it starts downloading these 22 files all over again. The problem is that I can't find these files after they're downloaded. The status bar in the bottom of the screen says: 4425 packages listed, 1069 installed, 0 broken, 0 to install/upgrade, 0 to remove.

---

### Post by Obor on 2006-09-18
> **BasNL said:**
> When I hit the reload button I get a pop up stating that it is downloading package information. 22 files to be exact. When I hit reload again after that, it starts downloading these 22 files all over again. The problem is that I can't find these files after they're downloaded. The status bar in the bottom of the screen says: 4425 packages listed, 1069 installed, 0 broken, 0 to install/upgrade, 0 to remove.

That looks like its working fine. Have you clicked on All - to show all packages? [Here is a wiki page about Synaptic]("https://help.ubuntu.com/community/SynapticHowto"), maybe it's worth looking through it.

---

### Post by BasNL on 2006-09-18
I've read the wiki, but unfortunately it can't help me with my problem... I need to get into settings -> repository to activate the universe repository, but synaptic won't let me because it keeps telling me *"The repository information has changed. You have to click on the "Reload" button for your changes to take effect"*

---

### Post by tatimmer on 2006-09-18
"tomsaptgetips" may help.

after you run "apt-get update" there should be a bunch of files located in /var/lib/apt/lists/.  I have found on ocassion that these files are deleted and replaced by a lock file.  Dont know why.

---

### Post by BasNL on 2006-09-19
> **tatimmer said:**
> "tomsaptgetips" may help.

after you run "apt-get update" there should be a bunch of files located in /var/lib/apt/lists/.  I have found on ocassion that these files are deleted and replaced by a lock file.  Dont know why.

Yes, you are absolutely right. There is a lock in that folfer. I tried to delete it but the system won't let me because it says I'm not the owner. Any ideas why?

---

### Post by tatimmer on 2006-09-20
you can delete any file with "sudo rm filename" .

"ls -al lock" will tell you the file is probably owned by root.

---

### Post by BasNL on 2006-09-21
I managed to get rid of the lock file thanks to your tip. But the problem still persists.

[IMG]http://i7.photobucket.com/albums/y261/BASSANOVA/Screenshot.png[/IMG]

I reloaded in synaptic after I deleted the lock file.
[IMG]http://i7.photobucket.com/albums/y261/BASSANOVA/Screenshot-1.png[/IMG]

Then tried to get into the repository settings once again, resulting in the same error.

[IMG]http://i7.photobucket.com/albums/y261/BASSANOVA/Screenshot-2.png[/IMG]

By the way... when I reload in synaptic, the lock file pops back into existance.

_____________________
update:

I just tried to do the new automatic ubuntu update, but that also doesn't work.:(  I says there a 8 new updates, then opens up synaptic, en winds up in the same cycle of errors as described above.

---

