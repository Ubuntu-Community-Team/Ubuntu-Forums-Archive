---
title: "We've read the guides, and we say &quot;Samba?&quot;"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by SRed13 on 2006-09-01
Now I've read that Samba is hard to configure.  I'm sadly forced to agree.  But maybe I'm just approaching this whole shabang from the wrong angle, let me explain my idea.

I have a Windows Network, wireless with WEP.  I had an old pc so I installed Ubuntu on it, now I'm trying to figure out how to setup a file server.  My idea is that I had an old wireless router laying around unused...so I'd use the Linux box as a file/program host.  I'd like to be able to switch networks, go to the linux thing and copy what I want.  I found a guide ( I googled "Linux file server for Windows" but the guide seems to have been slashdotted) for configuring Samba to run a small Windows network, it would create an H:\ drive on the user's pc, but I was more hoping to make an optional file server I could switch over to, copy files, then log out.  However, the guide involved user names and things and I really was just confused as anything.  

I'm an experienced Windows guy and I thought I could handle this, but all the guides I've looked over leave me confused.  

Bottom line: would it be possible for me to have an Ubuntu server that I could log into at will, and access files while remaining logged into Windows? 

If you just refer me to a guide, thats fine.  I wanna know Linux, I'm willing to get my hands dirty. 

And another question.  The whole "sudo root / su" thing.  I don't recall setting up a user name for Root when I installed linux.  Is that a default setting?  KNow of any good explanations for what root actually does?

Excuse my incompetence, I don't even remember when I knew as little about Macs or Windows as I know do about Linux.

-red

---

### Post by telegramsam on 2006-09-01
So you've installed it by now, and you have already networked the other machines, right?

You have the gateway and IP range from the other machines?

Are you running Gnome?

---

### Post by telegramsam on 2006-09-01
Well, anyway, I gotta run...

But if you're in Gnome and have Samba installed, go to Places>Connect to Server.

You'll be able to browse to the Windows (SMB) network from there.  Shared folders on machines that have had the network setup wizard run on them will show up.  You can browse the network and transfer files from there!

Good luck!

---

### Post by mssever on 2006-09-01
Root/sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Samba: It seems to me to be easier to run a Samba server on Linux than to mount Samba shares on Linux. There's a bunch of docs on the [Samba website]("http://www.samba.org"), but nothing spectacular that I know of. Perhaps a snippet of my /etc/samba/smb.conf will help. This is where the actual shares are defined. You'll also need to read through the file and make appropriate settings.
```
[DesktopHome]
path = /home/scott
available = yes
browseable = yes
public = no
writable = yes

[MP3]
path = /home/mp3
comment = MP3 Folder
available = yes
browseable = yes
public = yes
writable = yes

[ExternalHD]
path = /usbdrive
comment = External USB Hard Drive
available = yes
browseable = yes
public = no
writable = yes
```
Next, set up Samba users/passwords. Read [FONT=Courier New]man smbpasswd[/FONT] for info.

Finally, do ```
sudo /etc/init.d/samba restart
```

---

### Post by SRed13 on 2006-09-01
Thats the thing, I can't really say that Samba makes sense.  Linux detects the existing Windows network, and all the PC's can see the Linux network, but when I'd click from Windows to connect to it, I'm never prompted to log in at all.  I'm not sure where logging in would come in.  Perhaps the scheme of it makes it difficult.  Might it be easier to plug the Linux box into my existing Windows network and try making it a server from there?

---

### Post by mssever on 2006-09-01
> **SRed13 said:**
> Thats the thing, I can't really say that Samba makes sense.  Linux detects the existing Windows network, and all the PC's can see the Linux network, but when I'd click from Windows to connect to it, I'm never prompted to log in at all.  I'm not sure where logging in would come in.  Perhaps the scheme of it makes it difficult.  Might it be easier to plug the Linux box into my existing Windows network and try making it a server from there?

I'm not exactly sure what you're talking about. I'm no Windows expert, but is there really such a thing as a Windows network--or a Linux network? Isn't a network a network? I guess my question is this: Do you want to host the files on a Windows box or a Linux box?

---

### Post by SRed13 on 2006-09-01
Thanks for the into on roots, I think I see what I wasn't seeing before.  Awkward statement.  ANYWAY.

Would I be setting up the Samba accounts with everyone's existing Windows passwords?  Also, does the whole thing demand the presence of WindowsXPpro, as not all the pc's have it?  Your config file helped me to see how I'd format some of it, but do you think It might be better to just plug the Linux box into my router (it has a few wired ports) and just do things that way?  

Also, would the WIndows files need to be stored in a Swap folder?

---

### Post by SRed13 on 2006-09-01
> **mssever said:**
> I'm not exactly sure what you're talking about. I'm no Windows expert, but is there really such a thing as a Windows network--or a Linux network? Isn't a network a network? I guess my question is this: Do you want to host the files on a Windows box or a Linux box?
I guess I wasn't making sense.  A Network is only a network, what I was trying to infer as that I didn't want the users to have to log in more than once.  All files and programs the user would use is already installed on the pc.  I don't really understand where a user would need to sign in to the linux box in order to get the files.  Wanna just IM me?  I'm sosoii on AIM.

Prepares for a flood of pron.

---

### Post by crispy_420 on 2006-09-01
So if I understand you want a an Ubuntu box just to hold files. That can be easily done. Just search these forums for a guide on modifing the samba config file to allow other computers to access files.

If you want, after initial setup you can make this machine headless (no keyboard, mouse or monitor) and stash it out of the way (think closet). If you want to adjust or change something on this system you can access it from a VNC viewer. Also to simplify things it can be setup to auto login on a reboot.

As far as "root":

root = god

Root can do anything to your system. Change, delete, rename files at will. But the down side is you can render your system on reboot. By default Ubuntu does not have a root user that you can access at login. There is a root account but it has a random password set at install (someone correct me if I'm wrong).

So the sudo/su thing gives you temporary access to root functions without exposing your whole system. It is a safety thing.

It is late for me, but does this make any sense?

---

### Post by SRed13 on 2008-05-22
> **crispy_420 said:**
> 

As far as "root":

root = god

wordswordswords

It is late for me, but does this make any sense?

Awesome quote.  

I thought I'd let you guys know the progress.  That I made in three years or so.  about a day after posting this originally, I suddenly figured it out and low and behold, now my house has a full on server rack in the basement with a Dual P3 1 GHZ Server with 2GB ram running as the router for the house, on a Webmin Hardy Heron system.  Yah, I heart ubuntu now, all the way, its on my laptop, my tablet, my desktop, my sister's desktop at her house ( she doesn't realize its not windows and although I taught her nothing of it, has figured out apt-get )

So, yeah, thanks.

-red

---

