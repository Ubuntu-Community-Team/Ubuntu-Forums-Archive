---
title: "Help with Windows XP networking to Ubuntu through SMB"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2008-02-03
This is my first time so I would like very simple "1, 2, 3, etc" instructions for:[LIST]
[*]How to make Windows XP able to see the Samba shared folder.[/LIST]So far:[LIST]
[*]On my Ubuntu machine, there is a folder at /home/ryan/win that is shared through samba
[*]Other Linux on the LAN can connect just fine
[*]It seems invisible to windows however[/LIST]I would like to correct that last point if at all possible ;)

In addition, I am assuming that this *should* be as simple as making a folder and sharing it like I did.  How would I connect from windows (I know about "Map Network Drive", it didn't work either)
I am also assuming that there is no need for a username or password because I have not set up anythign like that for it, and all folder and file permissions in the folder are all on RWX.

---

### Post by spiderbatdad on 2008-02-03
i used this guide a while back, and it worked perfectly...except half way through, where in the linux set up, it gives non-octal permissions....0755 works fine, but you are mostly concerned with the windows side.[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)
I was using Gutsy. and setting up a share with windows xp.

---

### Post by Faud on 2008-02-03
.

---

### Post by ryanVickers on 2008-02-03
I didn't realize that you had to do anything to windows before.
It looks simple enough though... Would this set it up so that it works for all users on the computer, or only the one you use?

---

### Post by AaronLS on 2008-02-03
Does the drive hosted on the Linux system have to be NTFS?

---

### Post by jesrani on 2008-02-03
Hello. I have recently setup a Ubuntu desktop. I have it in a LAN with Win98 and Xp computers and have installed Samba, Winbind to connect to these.
I found this thread very useful to mount / unmount the shares automatically, hope it helps :
[http://ubuntuforums.org/showthread.php?t=637258](http://ubuntuforums.org/showthread.php?t=637258)
Now I am able to connect to the network shares when they are on and I use rsync to backup these to another hdd (formatted in ext3).
There are lot of posts on installing Samba in the forum. I dont remember the exact steps now.

---

### Post by ryanVickers on 2008-02-03
> **AaronLS said:**
> Does the drive hosted on the Linux system have to be NTFS?

I don't quite understand... its just a folder in the normal filesystem (ext3)

I would expect that Linux would handle the reading and writing of the filesystem, so windows could just view it as a generic network folder.

---

### Post by AaronLS on 2008-02-03
> **ryanVickers said:**
> I don't quite understand... its just a folder in the normal filesystem (ext3)

I would expect that Linux would handle the reading and writing of the filesystem, so windows could just view it as a generic network folder.

That answers my question.  For some reason I thought that drives that were used as network shares had to be NTFS formatted to be usable by Windows.

---

### Post by ryanVickers on 2008-02-03
wow, I went through the "[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)" ... it's embarrassing and completely unacceptable that *that* passes as the _official_ documentation!! :lolflag: :mad: ](*,)

---

### Post by ryanVickers on 2008-02-04
Well, after painstaking hours and hours after basically doing rand om things, I am now able to share folders on my Linux box among the LAN :D

I can't view windows shares yet, but Windows can view mine, and of course Linux to Linux works fine as well... always did though ;)

---

### Post by spiderbatdad on 2008-02-04
> **ryanVickers said:**
> Well, after painstaking hours and hours after basically doing rand om things, I am now able to share folders on my Linux box among the LAN :D

I can't view windows shares yet, but Windows can view mine, and of course Linux to Linux works fine as well... always did though ;)

IDK how official it is. It's just a wiki someone wrote...you could do the same. If you felt like posting your smb.conf, I could take a look at it with a fresh set of eyes. Seeing the windows files should be fairly easy so long as the windows side is set up correctly and you have:
In Explorer, find a drive or folder that you would like to share. In my example I will be sharing a folder at c:\shares. Right click the folder or drive and select Properties. Go to the Sharing tab and enable Share this folder. Enter a proper share name (shares in this example). Click Permissions and remove the Everyone group from the list. Now add the UbuntuSMB group (Add... and type in UbuntuSMB and click OK). Set the desired permissions for how Ubuntu should be able to access this share (in my example, I enabled full read/write access). This should mean that nobody is allowed to access the share, except for users in the UbuntuSMB group. If you explicitly press Deny on Everyone, that would also Deny UbuntuSMB since Deny has precedence over Allow and we don't want that.

---

### Post by Jerry N on 2008-02-04
I looked at the references here and have to say that I haven't had to do anything like all that stuff  on Ubuntu, Kubuntu, Linspire, Freespire, LinuxMint, and LinuxMint Fluxbox.  As soon as I install Samba and give it the correct workgroup, these Ubuntu distributions and their derivatives see the shared folders and files on the Windows machine.  To allow the Windows machine to see the Ubuntu shared folders without messing with passwords, I added the following right under [COLOR="Red"][global][/COLOR] in [COLOR="Red"]smb.conf[/COLOR] :
[COLOR="Blue"]
map to guest = Bad User
guest ok = yes[/COLOR]

I couldn't you tell why it works - I found it in the smb.conf for Freespire with the notation: 

#[I]The following lines are needed to allow file sharing without need for username and password
[/I]

Jerry

---

