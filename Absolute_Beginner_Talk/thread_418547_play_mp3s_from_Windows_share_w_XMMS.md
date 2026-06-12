---
title: "play mp3s from Windows share w/ XMMS?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by ilovebsod on 2007-04-22
Hello,

I'm pretty new to Ubuntu and Linux in general so please be gentle =)

I'm able to mount shares on my Windows PC and I can play mp3s from these shares with Feisty's default player (MoviePlayer) but when I try to play mp3s using XMMS the file info loads in the player, but the file doesn't player.  I've googled for quite a while and found many references to the same issue w/ no resolutions other than using a different media player or setting up a streaming server.  Neither of which appeals to me at this point.

Has anyone been able to get XMMS to play mp3s on a Windows share?  Any tips or directions on where to go from here?

Thanks in advance!

---

### Post by n3tfury on 2007-04-22
> **ilovebsod said:**
> Hello,

I'm pretty new to Ubuntu and Linux in general so please be gentle =)

I'm able to mount shares on my Windows PC and I can play mp3s from these shares with Feisty's default player (MoviePlayer) but when I try to play mp3s using XMMS the file info loads in the player, but the file doesn't player.  I've googled for quite a while and found many references to the same issue w/ no resolutions other than using a different media player or setting up a streaming server.  Neither of which appeals to me at this point.

Has anyone been able to get XMMS to play mp3s on a Windows share?  Any tips or directions on where to go from here?

Thanks in advance!

weird.  i don't have any issues using xmms and my windows share drive.

---

### Post by Jopjop on 2007-04-22
I'm not sure - but it could be a codec/plugin issue. I think XMMS uses its own brand of plugins for playback of different formats, whereas Totem uses ffmpeg/gstreamer or the like. Have you tried playing any mp3:s that are _not_ on your shared drive? Does XMMS play back any files at all?

---

### Post by ilovebsod on 2007-04-22
> **Jopjop said:**
> I'm not sure - but it could be a codec/plugin issue. I think XMMS uses its own brand of plugins for playback of different formats, whereas Totem uses ffmpeg/gstreamer or the like. Have you tried playing any mp3:s that are _not_ on your shared drive? Does XMMS play back any files at all?

sorry, I should have included that in my original post.  If I copy mp3s from my Windows PC to my Ubuntu PC XMMS plays the mp3s w/o issue.  it's only playing across the network that it does not work.

---

### Post by ilovebsod on 2007-04-22
> **n3tfury said:**
> weird.  i don't have any issues using xmms and my windows share drive.

when you say 'windows share drive' do you mean a disk that is physically attached to your Ubuntu workstation?  if so, the problem I am having is that I can't play mp3s across the network from a separate Windows PC.

---

### Post by n3tfury on 2007-04-22
> **ilovebsod said:**
> when you say 'windows share drive' do you mean a disk that is physically attached to your Ubuntu workstation?  if so, the problem I am having is that I can't play mp3s across the network from a separate Windows PC.

yeah, it's an NTFS formatted drive that's on the same box.

---

### Post by medley on 2007-04-22
> **ilovebsod said:**
> Hello,

I'm pretty new to Ubuntu and Linux in general so please be gentle =)

I'm able to mount shares on my Windows PC and I can play mp3s from these shares with Feisty's default player (MoviePlayer) but when I try to play mp3s using XMMS the file info loads in the player, but the file doesn't player.  I've googled for quite a while and found many references to the same issue w/ no resolutions other than using a different media player or setting up a streaming server.  Neither of which appeals to me at this point.

Has anyone been able to get XMMS to play mp3s on a Windows share?  Any tips or directions on where to go from here?

Thanks in advance!

This appears to be a known issue,  but hasn't been resolved. You cannot play a file over a samba share at the moment. Amarok doesn't work, and it's just a fancy frontend for xmms. I don't know if a fix is immenent or not. I have the same situation. Kind of sucks.

---

### Post by ilovebsod on 2007-04-22
> **medley said:**
> This appears to be a known issue,  but hasn't been resolved. You cannot play a file over a samba share at the moment. Amarok doesn't work, and it's just a fancy frontend for xmms. I don't know if a fix is immenent or not. I have the same situation. Kind of sucks.


damn.  that does suck.

can anyone recommend a music only player that is "lightweight" like XMMS but can play music over network from a Windows PC?

---

### Post by eli_d on 2007-07-22
i have had this problem before. XMMS will stream your mp3s through a windows network share, but you need to mount it first. see this thread: [http://doc.gwos.org/index.php/HowToM...resPermanently](http://doc.gwos.org/index.php/HowToM...resPermanently) for specific instructions.

it's a bit overwhelming at first (considering how much you have to do, just to play mp3s, but it's worth it in the end).

basically:

1) use synaptic to make sure you have the smbfs / smbmount command package. search for samba, you'll probably already have samba installed, but you will need the smbfs command.
2) create a directory on your desktop that will be the share mounting point
3) create a file in your root directory for your password / username information (gedit .smbpasswd... see instructions in link above for more detail)
4) mount the drive by entering something along the lines of:
Code:

sudo smbmount //elidesk/backup /home/eli/Desktop/elidesk -o credentials=/home/eli/.smbpasswd 0 0

5) open the directory on your desktop and your files should now be accessible and playable in xmms


this will not be saved when you restart your computer. so an additional step is to add your mount command line from #4 to /etc/fstab (the file that mounts all your drives when you start the computer) is necessary. see the link above for more specific instructions.

---

