---
title: "Question on Network Drives"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-05-16
What I want to do is, within my network, have a server (have an install of Kubuntu on it) and save videos/software on it, and access it from Windows, Mac, UNIX, and Windows computers, does anyone have any tips/a guide for doing this? Thanks

---

### Post by Happy_Man on 2007-05-16
Set up a SAMBA share, and then link to it from all your other comps. 

BTW, you mentioned Windows twice. :D

---

### Post by Peter1234123 on 2007-05-16
:O my bad, can I setup Samba from PuTTy, the server is hard, to say the least to physically access (behind around 60 LBS of other stuff and  cables all around.

---

### Post by duan on 2007-05-16
You can install and setup Samba to share everything like a windows fileshare, the mac can patch into a windows network without problems. But last time I checked it was a bit tough getting samba between mac/linux  plus  I have firewalls on both the mac and windows and it becomes a pain. (Mostly I never installed samba myself so I'm clueless)

I found it easier to just install ssh-server on my linux box and from the mac I rsync and get all the files I want. Google resently released a mac version of fuse, so you can 'fuse-mount' the entire disk or any folder of the linux machine as if it was a local thing on the mac, all through ssh.
I've used the native linux fusermount for similar uses between  linux boxes and it is absolutely brilliant, mostly because ssh is so easy to use.

On windows I ssh and rsync into the linux box through the cygwin utilities installed on the windows box.

I know a samba fileshare sounds simpler but windows networking is so dismal and from the mac it makes it very clear that windows sharing is unsafe but it will do it.

---

### Post by Happy_Man on 2007-05-16
I'm....not sure. Anyone else, feel free to jump in.

---

### Post by Peter1234123 on 2007-05-16
Heh, I may not even have to use SAMBA, I have OpenSSH server, and I pinged successfully to a Linux computer from my Windows PC, does that mean that I'm set?

---

### Post by duan on 2007-05-16
well...
ubuntu will respond to a ping, but port 22 needs to be open to accept ssh. if you install openssh you need to also install the server part otherwise port 22 stays shut on the linux box.
I think it is called openssh-server.

does putty have an ssh client? you can then just ssh to the same IP as you pinged.

You would have to ssh in as a specific user though:

ssh bob@192.168.1.1 

would be the command from a terminal. (even though it is openssh it is still the ssh command)

to get files across to windows if you have an rsync client on windows you can then just go:
rysnc -av [email]bob@192.168.1.1:/home/bob/big_video_archive/file.mpg[/email] .

or you can use "scp" the ssh copy comand if you have it on some windows utility
that will get the files across.

I'm at a loss if there is an equivalent fuse mount for windows.. hmm i'd like to use that too.

---

### Post by obrient on 2007-05-16
I would install Samba. It isn't too tough to get set up. I have it set up on my home network and share files between 3 Linux boxs, 2 Windows machines, and a Mac. The only time I have had problems is with the Mac, which once in a while has a problem. Though usually a reboot fixes it. 

I am not sure about using SSH I never really use it internally for moving files.

To use samba basically install samba which installs all of the files. Then you will need to set up the folder to share which you can access through the GUI (administration>Shared Folder) or by editing the smb.conf file. I then add a user, usually my normal user name and password, since I am not outside of my network. 

   1.  sudo smbpasswd -e username
   2. Type and retype new Samba password 

Once I am done with that I mount the share using the machines IP address. Then I am able to move files all over the place :)

Just my thoughts doesn't mean it is the best, but it works for me.

---

