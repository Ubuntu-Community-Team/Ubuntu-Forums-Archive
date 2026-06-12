---
title: "Deciding what to backup....."
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Midahed on 2007-08-22
I've been using partimage to create partition backups of my complete Feisty-based system.  However, recently I've been trying to move towards using tar instead - partly because I'll eventually need something other than a partition image when it comes to the next major system upgrade.

I know that backing-up my /home directory will get most of my data, but today I realised that isn't the complete answer.

I run a Windows guest under VMware Server for a couple of applications that I cannot move to Linux.  I've just discovered that my Windows data is effectively in a sub-directory of /var/lib/vmware-server (of all places).

I suppose the answer, in that particular case, is to backup my Windows data from within Windows, rather than relying on grabbing vmware's files, but how can I be sure that some other application doesn't also have important elements of my data stashed away other than in my /home directory?

Ideally I'd like to have a backup that I can be _sure_ contains _all_ my data and avoids the need to re-install all my applications if I ever have to use it.

Is this achievable, or am I on a hiding to nothing?

Thanks,

Mike

---

### Post by kidcharles on 2007-08-22
It is true that things can be a little distributed on a linux system. I would say the following directories in root are the most likely to have things you might miss if they were gone forever:

/etc: There are a lot of configuration files in here, most of which you will just replace in a new system, but a few might have some useful info in them (particularly something like /etc/X11/xorg.conf if you've made tweaks to your graphics)

/var: A lot of logs in here and as you found some files you might actually want to reference.

/usr: This directory often holds executables and files for programs, might be something useful in there too.

Most of the other directories in root are not something you need to back up (like /dev which is really links to your hardware). Take all this with a grain of salt.

---

