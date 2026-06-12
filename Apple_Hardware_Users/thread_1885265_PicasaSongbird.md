---
title: "Picasa/Songbird"
date: 2011-11-22
forum: Apple Hardware Users
---

### Post by canhoto on 2011-11-22
Hi.

Does anyone had success in using Picasa on a powerpc?
And what about Songbird?
I tried to build Songbird from source but without success.

Maybe Songbird (like iTubes) is quite replaceable by Rythmbox, Banshee, etc.

Picasa can be replaced by F-Spot or even better Shottwell or Digikam. But Shottwell seems to miss some Picasa features (like Geo-tagging, places, face-recognition) and DikiKam also, and DigiKam has quite a few bugs.


Thanks
So... Any suggestions or experiences with that?

---

### Post by pauljwells on 2011-11-22
I don't know if it is still the case, but Picasa was a Windows program that was bundled with an optimised WINE so that it would run on Linux. It's never going to run on PPC unless it has been completely recoded.

I don't know Songbird, but Clementine is in the repos for PPC (0.7.1) and it builds reliably from their development branch (0.7.3) with a lot of nice features.

---

### Post by canhoto on 2011-11-22
> **pauljwells said:**
> I don't know if it is still the case, but Picasa was a Windows program that was bundled with an optimised WINE so that it would run on Linux. It's never going to run on PPC unless it has been completely recoded.

I don't know Songbird, but Clementine is in the repos for PPC (0.7.1) and it builds reliably from their development branch (0.7.3) with a lot of nice features.

In the first place I want to rhank you for this[http://ubuntuforums.org/showthread.php?t=1816161](http://ubuntuforums.org/showthread.php?t=1816161) wonderful post. It has been very helpful to me in the last weeks (I have Firefox 8., Thunderbird 8.0 and LibreOffice running now).

I'm gonna try Clementine, although Rythmbox is not bad. I miss Picasa and I missed it already in my ppc Mac OS X (running on the same Power Mac in which I have Ubuntu). If the version you mention is a Windows Wine one, maybe it will not be so practical, maybe it will be slow. So maybe it's best to get used to Shotwell or DigiKam.

Thanks!

---

### Post by pauljwells on 2011-11-22
Clementine is probably the most actively supported music player at the moment. Rhythmbox is pretty much stagnant.

I don't think picaso could ever run on a PPC machine. WINE runs on x86 architecture only. I find Shotwell pretty good - similar to iPhoto, but then I'm only a 'holiday snaps' guy so I don't know how a serious photographer would find it.

For Clementine, follow their instructions. You need to install Git and clone the source directory, and then it's a simple ./configure, make, sudo make install deal. The binary ends up in /usr/local/bin and the first time you have to run from a terminal. Pin the tile to the unity bar and then it will start form there like any other app. You don't need to try to build a .deb. It worked on 11.04, not tried on 11.10. It even integrates with the volume control like Banshee.

---

