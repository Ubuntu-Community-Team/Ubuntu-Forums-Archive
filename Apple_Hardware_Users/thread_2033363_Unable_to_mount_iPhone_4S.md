---
title: "Unable to mount iPhone 4S"
date: 2012-07-26
forum: Apple Hardware Users
---

### Post by t103z on 2012-07-26
I am using ubuntu 12.04 64bit and tried to mount my iPhone 4S (ios5.1.1,jailbroken). However I got the following error
> DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)I have already installed the latest version of libimobiledevice and I've tried this:

sudo add-apt-repository ppamcenery/ppa 
sudo apt-get update
sudo apt-get dist-upgrade 

and this:

idevicepair unpair 
idevicepair pair 
devicepair validate

but still won't work. Can somebody help me?

---

