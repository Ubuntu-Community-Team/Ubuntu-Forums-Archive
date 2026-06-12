---
title: "Avahi, firefly (mt-daap) - serving files to itunes"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by jd65pl on 2008-01-10
I have set up firefly (mt-daap), it is running and I am able to configure it through the web front end, I am sure everything is OK with firefly, avahi is not announcing any of the services on the server, smb, nfs, http, mt-daap... etc I am well and truly struck.

Has anyone got firefly  Version svn-1586 working on gutsy? if so what are the steps you took?

Or can someone tell me how to make avahi announce the services on the machine?

Thanks

---

### Post by jd65pl on 2008-01-11
I am now able to share my music with itunes on my mac book here is my how to which brings serveral other guides together and adds a few other pieces. If you are running gusty and wish to share music with other linux boxes using amarok or rhythm box this solution is ideal.

[Here]("http://jamiedumbill.com/index.php?page=28") is a link

---

### Post by njparton on 2008-01-16
Hi, I'm trying to do this at the moment.

Did you use the mt-daap in the repos or the latest .deb from the developers site?

I've even tried compiling the latest version from source but I still can't get it to work.

I'm using gutsy 64 bit - I wonder if that's the issue?

---

### Post by jd65pl on 2008-01-16
I'm using the version from the repos, can you see the share through amarok or rhythm box on your gutsy machine? I am also using gutsy 64bit.

---

### Post by njparton on 2008-01-16
I can't even get it to parse the config file at the moment. It was winging about the databse type specified (fixed now I think) and now I have issues with the mp3 directory.

I think the latter may be due to spaces in the path.  I don't really want to change that as I'd have to refresh itunes, so I'm hoping a symbolic link will do the trick.

I think I also have issues because I've tried both the repos version and the latest stable build. I can't work out how to remove the latter and just work with the repos version.

I've not attempted to open the relevant port in iptables yet either.  I ran out of time last night, planning on having another go tonight...

---

### Post by jd65pl on 2008-01-16
If you have a your music on an NTFS drive then you could have problems. 
For some windows formatted drives (i.e. an external hard drive formatted for windows) only user permissions are available.   
You must go to /etc/mt-daapd.conf and change *runas* to be the same user that has rights to the files on the drive.  
If you are having trouble with source, the debian package is always available (for stable)

---

### Post by njparton on 2008-01-16
It's an ext3 drive that I moved "My documents" to.  My itunes library sits under that and then "my music" hence the potential issue with the path name.

I'll try creating a symbolic link from the root of the drive tonight, and if that doesn't work then I'll move my complete itunes library to the root of the drive and then face having to reconfigure itunes (which never seems to be as simple as it should - I always end up with it re-reading all the files in).

I first need to work out how to get rid of all the mt-daap versions I've been playing with to start afresh tonight.

I removed the one from the repos via synaptic, but the one I compiled is still there. In theory, could I just go around manually deleting all the mt-daap files as root user?  At the moment it won't run because of a conflict, not the config file (although it will fail there too).

---

### Post by njparton on 2008-01-16
Hmmm, can't find a deb file for the AMD64 architecture on their website - can anyone help?

The one in the repos doesn't seem to work for me.

---

### Post by njparton on 2008-01-16
Finally got it working.  Had to use webmin to configure iptables though.

---

