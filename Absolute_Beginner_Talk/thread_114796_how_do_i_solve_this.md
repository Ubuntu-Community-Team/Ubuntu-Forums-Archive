---
title: "how do i solve this??"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by poloman2 on 2006-01-09
I have just finished installing ubuntu.. but once I log in I get the following message:

"Could not look up address for "servername" 
This will prevent GNOME from operating correctly. It may be possible to correct this problem by adding "servername" to the file /etc/host."

I dont know what to do here...
some things dont work...

---

### Post by Arktis on 2006-01-09
I used clusty to search for this error message.  It's possible something went wrong with your hostname during the installation (whether it was you of a bug in the installer or both, I have no idea).  My understanding is that you need to add your hostname to /etc/hosts.

There are some seemingly relvant results by searching for ***"It may be possible to correct" /etc/host*** in google, clusty, or some other search engine might do as well.  Sorry I can't be more help than that.

---

### Post by Mustard on 2006-01-09
To edit the /etc/hosts file, you would need to get to a root prompt (as your sudo command will not be working with a misconfigured hosts file). The easiest way to do this is to use the recovery mode option from the grub menu at bootup.

When you get to a root prompt, open up the /etc/hosts file with this command.

```
nano /etc/hosts 
```

The /etc/hosts file normally looks something like this...

```
127.0.0.1       localhost.localdomain   localhost       slave

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

What you need to do is to edit the first line so that it contains a hostname for your computer.  Mine is called 'slave' as you can see above.  You can choose any name you like.  The current hostname can be found by using the 'hostname' command. By default ubuntu uses the hostname 'ubuntu'.

The first line should look something like this if you were using the hostname, 'ubuntu' for example..

```
127.0.0.1       localhost.localdomain   localhost       ubuntu
```

An additional command you can look at with regards to hostnames is this command below.

```
hostname #returns the current hostname
hostname <hostname>  #sets the hostname according to the value entered for <hostname>
```

This may tell you what your current hostname is, even though your /etc/hosts is misconfigured.  I would be curious if it does, as I haven't had the opportunity to try it yet with a misconfigured hosts file, but I have seen it recommended in another thread somewhere.

---

