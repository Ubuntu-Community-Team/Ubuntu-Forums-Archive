---
title: "Bizarre Samba Behaviour"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by BitTorrentBuddha on 2006-02-28
Well, I've been using Samba improperly for a month or so now, (I could access some files but never used a password) and files on the windows network just kept dropping away from what I could access. And what I would like to know is what password do I put in to access the windows files. The windows machine can access the ubuntu files using the samba password set up in smbpasswd but the ubuntu machine can't access the windows files using that password/username combination, is this strange or am I just completely unaware of my surroundings and using the wrong password to try to access the windows box?

---

### Post by BitTorrentBuddha on 2006-03-02
bump:(

---

### Post by Dylan103 on 2006-03-02
Bump because I have same problem

---

### Post by stalefries on 2006-03-02
There should be a password set on the Windows machines for the files they are sharing. Find out that one.

---

### Post by dickohead on 2006-03-02
You can also set windows to share the files as read/write, also you can set the everyone group to have access to the files, this will include network users. You could stuff around with users and passwords, but I'd just share the folder to everyone and work back from there. If it still isn't working correctly, what version of windows are you sharing from?

---

### Post by BitTorrentBuddha on 2006-03-02
xp, and I can't figure out where I can set up a password

---

### Post by dickohead on 2006-03-02
xp home or pro? XP Home has very limited networking capabilities.

---

### Post by BitTorrentBuddha on 2006-03-03
home I'm afraid, and all I'm trying to do is access the printer and the files on the computer

---

### Post by Iowan on 2006-03-03
How is Samba set up to share - security=user?

---

### Post by racecat on 2006-03-03
Try using the login and password you login under on your XP box. If there is no password, just the login name. This has worked for me on XP home and 2000 Pro.

Good luck,
Bill

---

### Post by BitTorrentBuddha on 2006-03-03
yeah, i've got
```
;   security = user
```
with the semicolon

---

### Post by BitTorrentBuddha on 2006-03-03
The login passwd/username didn't work either = \

---

### Post by racecat on 2006-03-04
I don't know much about Gnome, but I've used xfce, which was a little buggy with network access. I now run KDE and it is much better. The things I've seen:

Install samba, smbfs, and smbclient. You have to reboot after installing smbfs for it to take effect.

The first time I tried to find other machines, it wouldn't until I accessed the new one from them. It probably has to do with tables, but this was an easy solution.

I am able to log in to the Windows machines using the Windows machine's login/ password.

Setting up for a printer located on a Windows machine is pretty straight foreward. I did it with Gnome a long time ago; More recently with KDE. Just set the printer to share on the Windows box and put in the appropriate share name on the Ubuntu box when prompted. You probably need to establish the network connection first.

Sorry if I'm a little ambiguous. I'm working from memory. I need to make good notes, but I never remember to do it.

Good luck and have fun,
Bill

---

### Post by knalle on 2006-03-04
[QUOTE=BitTorrentBuddha]yeah, i've got
```
;   security = user
```
with the semicolon[/QUOTE]

try to remove the semicolon and restart samba

```

sudo /etc/init.d/samba restart

```

and use smbpasswd to set the password in windows encrypted format for samba;

```

sudo smbpasswd username

```

---

### Post by BitTorrentBuddha on 2006-03-04
that didn't solve the problem = \
once again, I'm having trouble accessing files on the windows computer, accessing ubuntu files the windows box doesn't provide any problem

---

### Post by BitTorrentBuddha on 2006-03-05
bump

---

### Post by racecat on 2006-03-05
In the wee hours this A.M., I remembered having a problem like I think you are describing. It was with a minimal Breezy load I played with. It was a server installation with just Xfce4 and a few Gnome and KDE apps I like. Every time I tried to log into a Windows box, it just came back with a new login screen. I don't remember the exact syntax of any errors. I've since scrapped it and am now running Kubuntu with no problems.

I did a little research on the forums and found this. It seems to be a common problem:

[http://ubuntuforums.org/showthread.php?t=83300&highlight=smbfs](http://ubuntuforums.org/showthread.php?t=83300&highlight=smbfs)

I haven't found any solutions, but I'll keep nosing through. It looks like you can run smbclient from the command line to accomplish file xfers, etc., but I haven't gotten very far with that.

Bill

---

### Post by knalle on 2006-03-05
[QUOTE=BitTorrentBuddha]
once again, I'm having trouble accessing files on the windows computer, accessing ubuntu files the windows box doesn't provide any problem[/QUOTE]

ah ok, but you know SAMBA got nothing to do with this then, its **smbfs** and **mount**

happy hacking

---

### Post by racecat on 2006-03-05
I may have found a solution:

[http://ubuntuforums.org/showthread.php?t=122018&highlight=smbfs](http://ubuntuforums.org/showthread.php?t=122018&highlight=smbfs)

It looks like I'm not having a problem because Konqueror handles the mount for me (???). Anyway, it may be worth a try. I did a search under "smbfs" and found lots of posts. It takes a while, but there is a wealth of info. I found some that mentioned permanent mounts so you don't have to do this. Also I found in Synaptic an app called linneighborhood (I think) that is a network neighborhood type browser. I haven't tried it (I have that feature built in to Konqueror).

Good luck with it.
Bill

Edit: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by BitTorrentBuddha on 2006-03-05
but I don't want it mounted, I want the password they prompt for as I need that password to access the printer using cups as well...

---

### Post by BitTorrentBuddha on 2006-03-06
bump:(

---

### Post by racecat on 2006-03-06
I'm a little surprised no one else has seen this. One of the threads I listed in a previous post was talking about what may be a similar problem to yours. Please clarify for me. Does the login box just keep coming back after you fill in the blanks and hit enter? If so, that sounds like the same problem I saw with a Ubuntu Breezy load and I found references to in my searches.

I'll tell you what. If you don't have a solution by the weekend, I'll try to replicate it (time permitting) and see what I can come up with. Be patient. I think the solution is out there.

Bill

---

### Post by BitTorrentBuddha on 2006-03-07
this thread, [http://ubuntuforums.org/showthread.php?t=71125](http://ubuntuforums.org/showthread.php?t=71125) , seemed to have what i was looking for on the second post, but it was never solved :-? and the other solutions are all using a mount, but I need this password to plug into cups so I can access the printer.

---

### Post by FizDev on 2006-03-08
I had a similar problem and solved it... all I did, is enter the name of the network you want to connect to in the username area and leave the password area empty, then it should work correct. Don't ask me why, but it worked ;) 
Good Luck!

---

### Post by deBaas on 2006-03-08
Forget samba, it's for sharing files. NOT for accessing shares on other pc's.

---

### Post by racecat on 2006-03-08
I stopped at my local computer mega-store to pick up a network switch for a customer, and visited the used computer store next door. Long story short, I scored a used minimal pc for $50 and loaded up Ubuntu. Conclusion, Nautilus blows. It could see the other Ubuntu box and the workgroup for my Windows boxes, but couldn't get past that. It just came up with domain logins for the Win-boxes and never took them. I loaded Jags and xsmbrowser. Jags crashed, but xsmbrowser found the two workgroups I have (1 for Ubuntu and 1 for Windows). From there I was able to select a box, fill in the login and password, and browse til my heart's content. I was able to "save" a file from another box to the Ubuntu box, but ran into some problems moving files the other way. The file "emptied". It probably works if you do it right, but I suggest you experiment with test files. There are probably better browsers out there, but it worked.

FizDev, what "network name" did you use? Is that the network IP address, domain name, workgroup name? I'm curious. Once you get connected, Nautilus is probably a more intuitive  and useable browser than xsmbrowser. I may try to enable the other repositories and find a better one.

Hope this helped.
Bill

---

### Post by BitTorrentBuddha on 2006-03-09
I'm not using cups, rather samba, for printer sharing if it weren't previously obvious, just you correct myself.

and to _see_ the share off of samba I have to use it as a location in nautilus (nautilus smb://<network_computer_ip_or_hostname>)

---

### Post by FizDev on 2006-03-13
[QUOTE=racecat]FizDev, what "network name" did you use? Is that the network IP address, domain name, workgroup name? [/QUOTE]

I used the workgroup name.

---

