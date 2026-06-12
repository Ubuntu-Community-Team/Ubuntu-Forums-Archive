---
title: "Music File Access by Windows and Mac"
date: 2005-08-24
forum: Absolute Beginner Talk
---

### Post by haze03 on 2005-08-24
Ok I have been searching, but since I am kind of still clueless I think individualized help may be needed.  Anyhow, my primary reason for setting up linux (ubuntu) was as a file server so I can access my music between my powerbook and my windows desktop and because my desktop didn't have the space for a couple 200 gb drives.  So I have samba set up, I was able to transfer files from the windows box through ubuntu, but can't access the ubuntu box in windows.  I changed the workgroup to match, but i get an error saying incorrect password.  However, more importantly what is the best method for this?  Do I just share a directory with samba?  Mac OSX doesn't use samba, correct?  I came across a lot of stuff to us mt-daap for an itunes server, but I don't like itunes.  No gapless playback, limited codes, etc.  I use it on powerbook, but mostly play music in foobar with windows.

So the short of it is - what do i need to do to store all of my music on the ubuntu box, but play through windows and macosx?  Make it easy for me and be specific because I am still a linux dummy.  

Thank You

---

### Post by invisage01 on 2005-08-24
seems like you have to set up your folders for sharing.. 
try:
[http://www.ubuntuguide.org/#sambaserver](http://www.ubuntuguide.org/#sambaserver)

---

### Post by haze03 on 2005-08-25
Yeah i did that, but still seems like there must be a better way.  Something better.

---

### Post by Nequeo on 2005-08-25
Try opening up Synaptic and then search for and and install 'libapache2-mod-musicindex'. 

From the description:
> 
Browse, stream, download and search through MP3/Ogg files
mod_musicindex is aimed at being a C implementation of the Perl module
Apache::MP3 ([http://search.cpan.org/dist/Apache-MP3/)](http://search.cpan.org/dist/Apache-MP3/)).
It allows nice displaying of directories containing MP3 or Ogg Vorbis and
FLAC files, including sorting them on various fields, streaming/downloading
them, constructing playlists and searching.


In case you didn't know, apache is an open source web-server. So you'd be able to view your MP3 collection in the web-browser of your choice, and create playlists to have streamed to your media-player of choice. I've never used it, however, so I can't give you step-by-step instructions for setting it up. 

Nevertheless, I'm sure there are plenty of people out there who have... So just post back here if you have any problems getting it to work.

Cheers!

---

### Post by nad on 2005-08-25
libapache2-mod-musicindex looks interesting, but, as it requires setting up an apache server, it may be overkill and will certainly take some configuring.

Darwin is UNIX(tm) based. Its' samba implementation works just fine. You will be able to bring up your share in Safari.

The short of it is that to use samba, you need to create a share and configure your smb.conf:

[share1]
   comment = Music server's music
   writable = no
   locking = no
   path = /music
   public = yes

Where share1 is any name and path = is the mount point of the share1 directory. You will also need to set up samba accounts, passwords and adjust permissions.

---

### Post by haze03 on 2005-08-25
I have samba setup with permissions.  All three computers have the same user account and password.  I change dteh workgroup on unbuntu to be the same.  I can see my windows pc from ubuntu and login into the windows system from ubuntu and transfer files.  However, I can't access the ubuntu pc from windows.  Sometimes it doesn't show up and when it does it says the passowrd is incorrect.  though it is not.  Obviously I want ubuntu to be the server and I don't want to have to touch it much.  I want it to see it in the closet or somewhere and be able to access it from my other computers and send files to it after I rip them and to access them when I want to play them.  Perhaps samba is teh best and I just have it setup wrong.

---

### Post by nad on 2005-08-25
Have you set up samba user accounts and passwords. This needs to be done explicitly with the smbpasswd utility. They may be configured to be identical to your ubuntu user account. It is these account user names and passwords that must be used, not your ubuntu user account, to access the samba shares.

---

