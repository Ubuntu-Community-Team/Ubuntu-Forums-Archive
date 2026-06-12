---
title: "Using cdrecord from command line cant read disc"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by PhilJ on 2007-03-29
Hi all,
      I can burn a cdrw no problem using Gnomebaker, but if I try to burn one using cdrecord command line like

cdrecord -v -eject -tao speed=12  (filename)

the cdwriter starts up the red light comes on and it appears to burn. The normal messages from cdrecord (the ones you get in the details box in Gnomebaker) are listed in the terminal but I cant read the completed disc. This is just me trying out command line and script options, I was brung up on dos and showing my age.Can anyone show me where I'm going wrong and/or  give me an example line I can work from? I've searched the forums but cant seem to find what  I'm looking for. Cant find it in the man pages either , I'm missing something really simple.

thanks

Phil

will have to call back later and check for replies so if I dont reply straight away I'm not being ignorant, got to go out.

---

### Post by tatimmer on 2007-03-29
I burn audio and data cd's using cdrecord. Check out the tip file on my website. 

For audio cd to burn all .wav files in current directory:
sudo cdrecord -v speed=8 dev=/dev/hdd -audio -tao -pad *

I follow a 2 step process to make a data cd:
[1] mkisofs -R -v -o file.iso  dir1 dir2 dir3
The first step bundles all the data files into 1 .iso file including the iso file system.
[2] sudo cdrecord -v -dao speed=8  dev=/dev/hdd  -data  file.iso

---

### Post by PhilJ on 2007-03-30
thanks tatimmer,
much obliged for your reply. apologies for delay in reply just got back. will try your suggestions.

thanks again 

philj

---

### Post by PhilJ on 2007-03-30
me again,

ran cdrecord -scanbus and it returned error

cant open  /dev/pg* and I got no output. cdrecord seemed to work anyway using /dev/hdc but then I got an error incorrect coding in markthomas.wav the file I was attempting to burn to cd. This file I recorded from a rpm stream from the BBC using Audacity like I always do with something like this. Is there some difference in codecs for wav files from app to app? the file burned OK using Gnomebaker after Gbaker converted it from wav to cda .

I know these are not earth shatterinly desperate queries but I am curious 

thanks again

Philj

---

### Post by PhilJ on 2007-03-31
bump and recommend you check out tatimmer's website too

---

