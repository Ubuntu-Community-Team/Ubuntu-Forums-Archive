---
title: "Help: Can not upgrade to Gutsy!"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by PC_load_letter on 2007-10-21
Hi all...Since Gutsy was released I was experiencing an error from the update manager as follows:
-------------------------------------------------------------------
[B]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:) 302 Found[/B]
-------------------------------------------------------------------------

So, I thought it was due to the servers having bandwidth problems as everyone is upgrading. Now 3 days after the release I am still having the same error when I launch the update manager + when I thought I'd go ahead and upgrade to Gutsy I got the following error:
--------------------------------------------------------------------------
[B]Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found[/B]
-----------------------------------------------------------------------------
I am running Ubuntu 7.04 amdx64bit and I am in the US (i.e. I have the US repositories selected in Synaptic). My desktop PC is connected to the web via a Linksys router and a Motorolla cable modem. Other than this error I have no problem what so ever in surfing the web. 

Any idea how to fix this? 
Thanks.

---

### Post by GSF1200S on 2007-10-21
> **PC_load_letter said:**
> Hi all...Since Gutsy was released I was experiencing an error from the update manager as follows:
-------------------------------------------------------------------
[B]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:) 302 Found[/B]
-------------------------------------------------------------------------

So, I thought it was due to the servers having bandwidth problems as everyone is upgrading. Now 3 days after the release I am still having the same error when I launch the update manager + when I thought I'd go ahead and upgrade to Gutsy I got the following error:
--------------------------------------------------------------------------
[B]Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found[/B]
-----------------------------------------------------------------------------
I am running Ubuntu 7.04 amdx64bit and I am in the US (i.e. I have the US repositories selected in Synaptic). My desktop PC is connected to the web via a Linksys router and a Motorolla cable modem. Other than this error I have no problem what so ever in surfing the web. 

Any idea how to fix this? 
Thanks.

Open up sources.list:

```
sudo gedit /etc/apt/sources.list
```

and put a # in front of every medibuntu entry. You have to disable 3rd party repos before an upgrade...

**EDIT** Do a sudo apt-get update after this. You should actually REMOVE the medibuntu entrys from the sources.list, go to the medibuntu website and reload them with the version that specifies Gutsy, just so that you run the right repos...

good luck :)

---

### Post by PC_load_letter on 2007-10-21
Thanks a lot. One slightly unrelated question though. Is it possible to install Gutsy side by side with my current 7.04 Feisty? It took me a lot of time and effort to optimize the current version. 
If it is indeed possible, what do I need to do, a clean install from the Gutsy Live CD? 

Thanks.

---

### Post by GSF1200S on 2007-10-21
> **PC_load_letter said:**
> Thanks a lot. One slightly unrelated question though. Is it possible to install Gutsy side by side with my current 7.04 Feisty? It took me a lot of time and effort to optimize the current version. 
If it is indeed possible, what do I need to do, a clean install from the Gutsy Live CD? 

Thanks.

Sorry, I didnt notice you posted earlier... :(

Do you currently dual boot with windows? If so, it is definitely possible to triple boot, although it does require you to manually edit your grub config (not that hard). The partitioning would not be that bad. So short answer is yes, with just a little work.

If you just have Ubuntu Feisty, it would be very easy, simply put in the Gutsy LiveCD and resize the current ext3 partition, and install. 

Did you happen to partition a seperate /home partition? That would really be awesome in this case, because you could easily access files and program config folders from both the feisty and gutsy install! You might consider this for future versions, so that you can more simply wipe and reinstall...

---

### Post by Paqman on 2007-10-21
I set up Gutsy alongside Feisty for testing the beta. Couldn't have been simpler, just make a new partition and install. I still have my Feisty on there gathering dust, actually.

A separate home is great for this setup. Just remember that if you're going to set up the same users on both that you'll have to make sure you give them the same user number. If they're different you'll get file permissions problems on the files in /home.

---

### Post by PC_load_letter on 2007-10-21
Thanks a LOT, I really appreciate it. I currently dual boot with WIndoze XP Pro, just use it for my VST music stuff and will ditch it the day I can easily install Jackd :D
I think I'll not rush into installing Gutsy, and will definitely keep my Feisty. 
Thanks again.

---

