---
title: "Streaming files over Windows Network"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Eduardo Serra on 2007-04-11
Hey guys, I have a windows PC sharing most of my multimedia files.... on my ubuntu desktop I can see and copy all of them and everything works fine except when I just double click to play them over the network, the only way I can get them to work is by copying them onto the ubuntu pc.... I have tried VLC, Totem and xmms, but non work.... is there any way to do this?? Im talking about mp3s and xvid videos... thanks in advance

---

### Post by Eduardo Serra on 2007-04-11
Oh, and also, is there any way I can add the ubuntu desktop to my windows workgroup and share files just like on any windows pc?

---

### Post by farscape on 2007-04-11
I currently stream a playlist of over 1000 songs from an external HD attached to my windows(XP) machine. I use Rythmbox. The only way I could get the media player to import the playlist is for the windows shares show up in my linux file structure. That way I could browse to the share and add folder or file to playlist.
The only way I could get the windows shares to show up in my linux file structure is to set up a permanant mount using smbfs.

Check this out: [HowToMountsmbfsSharesPermanently]("http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently#Mounting_smbfs_Shares")

---

### Post by Eduardo Serra on 2007-04-12
Well, im new to this so I did a bit of research and found this video [http://www.ubuntuvideo.com/file_sharing_with_ubuntu_6_10_and_samba](http://www.ubuntuvideo.com/file_sharing_with_ubuntu_6_10_and_samba)

I cant follow it though cause during the process it automatically has to download some files (samba and something else) but it always fails!.... a friend told me I have to add some repositories or someting... anyone?

---

### Post by farscape on 2007-04-12
Add repositories. **System>Administration>Synaptic Package Manager**.
When Synaptic opens, go to **Settings>Repositories**.
Under the Ubuntu 6.10 tab, check everything. 
Click close then Click the **Reload** option on the toolbar.
You should be ok as far as repositories.

I am very new to this also and the first thing that I needed Ubuntu to do was stream movies(XviD/DivX) and music(mp3/ogg) from a windows share. I got it with smbfs.

Hope this helps

*Now all I need is a Linux usnet newsreader that is as good as Newsbin Pro. It dosen't exist........yet*

---

### Post by Eduardo Serra on 2007-04-12
Ok, nevermind about the repositories thing... I got it to download the samba software.... I followed the video tutorial step by step and now Im able to share files from windows to ubuntu and from ubuntu to windows.... I still am not able to listen to an mp3 or watch a video that is stored (and shared) on the Windows machine except I copy and paste it on the ubuntu computer (which is not practical at all).... for some reason if a share an mp3 stored on ubuntu Im able to listen to it on the windows machine.... is there anything special I need to do??

---

### Post by Eduardo Serra on 2007-04-12
What does it mean to "permanently" mount the shares?? how would they not be permanent?

---

### Post by farscape on 2007-04-12
> **Eduardo Serra said:**
> What does it mean to "permanently" mount the shares?? how would they not be permanent?

Remember, I'm still learning here. 

What Permanently mounting shares means to me...

WHen I started on my quest to stream music from a windows box, I found out that most if not all linux media players will only browse local files. So I couldn't even get off my own hard drive through the browsing capabilities of the player. You know how in windows you can add music to a playlist by browsing your drive and the network through network neighborhood. It dosen't work that way with linux.(I think)
I had to make my windows shared folders a part of my local file system. I did this with a permanent smbfs share. It mounts the shares when linux boots. The shares show up in my local directory and I can import them as a playlist. Hope that made sense.

How do you browse to your windows shares? I mean where do they show up?

---

### Post by Tylo on 2007-04-14
There is a great tutorial here on how to set up Samba: [http://www.testmy.net/t-11663](http://www.testmy.net/t-11663)

Ultimately, you end up mounting the shared drive from **My Computer->Tools->Map Network Drive..** Once you are in there you put **\\pathToLinuxSharedFolder\** in the Folder dialog and you're good to go.

The Samba setup is based on a Bonzai distribution ( a Debian based distro ). Personally, I haven't tried it in Ubuntu.


Also, if you are interested in steaming music, check out this: [Jinzora]("http://www.jinzora.org/")

---

### Post by Eduardo Serra on 2007-04-15
My Computer->Tools->Map Network Drive.. Once you are in there you put \\pathToLinuxSharedFolder\ in the Folder dialog and you're good to go.

But that only makes the shared folder on ubuntu a network drive on the windows computer.... what I want is a shared folder on windows to be accessed as a drive on ubuntu

---

### Post by Eduardo Serra on 2007-04-15
> **farscape said:**
> Remember, I'm still learning here. 

What Permanently mounting shares means to me...




How do you browse to your windows shares? I mean where do they show up?
I go to places network servers, and I can see my local network, and all of my shared files on windows.... I have been able to do that since day one on ubuntu, without samba or anything

---

### Post by Eduardo Serra on 2007-04-15
Ok, my windows pc's login name is Principal and the computer's name is AMDX2, I log in with no password.... Im trying to mount a whole drive (its already shared on windows) F...... heres what I type on the terminal and heres what im getting

> nacho@nacho-desktop:~$ sudo mount -t smbfs //AMDX2/F /home -o username=Principal,password=
mount: wrong fs type, bad option, bad superblock on //AMDX2/F,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by pognonec on 2007-04-15
I got a similar problem, but curiously, only with videos (mp3 stream fine).
See [http://ubuntuforums.org/showthread.php?t=403613](http://ubuntuforums.org/showthread.php?t=403613)
For mounting, you may simply do: Places/Connect to server...
just enter the name of the remote box (or IP address), and it will magically and definitively appear on your desktop.
But I still cannot play video through my LAN...

---

### Post by Eduardo Serra on 2007-04-15
..... So thats what mounting is?? I have already done that... so I guess ubuntu just doesnt do it?

---

### Post by two_wheels on 2007-04-15
You can do this, I use this same setup every day, streaming MP3's from a Windows network.  But it absolutely would not work until I edited the smb-module.conf file as described here:

[http://ubuntuforums.org/showthread.php?t=315333](http://ubuntuforums.org/showthread.php?t=315333)

Even for Feisty you need to do this.

I hope this helps!

---

### Post by Eduardo Serra on 2007-04-16
Ok, so I did that... but apparently this only works with Totem Movie player.....but Totem isnt working for me (its not even working for files stored on ths ubuntu desktop so this has nothing to do with the network streaming problem).... every time I try to play either a mp3 or xvid movie I get an error message .... "You do not have a decoder installed" blah blah .... what should I do???..... I still would preffer to play all my music (local and streaming) from xmms and all my videos from vlc.... but non of those two work for local network streams apparently

---

### Post by farscape on 2007-04-16
> **Eduardo Serra said:**
> Ok, so I did that... but apparently this only works with Totem Movie player.....but Totem isnt working for me (its not even working for files stored on ths ubuntu desktop so this has nothing to do with the network streaming problem).... every time I try to play either a mp3 or xvid movie I get an error message .... "You do not have a decoder installed" blah blah .... what should I do???..... I still would preffer to play all my music (local and streaming) from xmms and all my videos from vlc.... but non of those two work for local network streams apparently

make sure you have added(checked) all the available repositories. Then copy and paste this into  a terminal window.

[B]sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs[/B]

Also, checkout this How To. [ How to install Multimedia Codecs]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Codecs")


Adding all Repositories: In Synaptic Package Manager: SETTINGS>REPOSITORIES: On the Ubuntu 6.10 Tab, Make sure everything is checked. Then hit reload.

---

### Post by two_wheels on 2007-04-16
> but apparently this only works with Totem Movie player.....

I am using Rhythmbox.... haven't actually tried playing the network files with anything else though.

---

