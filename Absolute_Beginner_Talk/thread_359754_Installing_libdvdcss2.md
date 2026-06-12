---
title: "Installing libdvdcss2"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-02-12
Hello, I have been trying to install libdvdcss2 but without success from here:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

> *      Installing libdvdcss2
*            Install the libdvdread3 package.
*            Download and install the libdvdcss2 package after adding the repository [here](http://medibuntu.sos-sts.com/repository.php)
*            Your DVD player should now play back encrypted DVDs.

I can't figure out how to add the repository. Could anyone give me some insight?

Dr Small

---

### Post by Maestro23 on 2007-02-12
> **Dr Small said:**
> Hello, I have been trying to install libdvdcss2 but without success from here:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)



I can't figure out how to add the repository. Could anyone give me some insight?

Dr Small

Repositories are kept in your[COLOR="Red"] /etc/apt/sources.list[/COLOR] You need to edit it.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Dr Small on 2007-02-12
Well yeah, I basically had an understanding of that much, but WHAT to put in the /etc/apt/sources.list is the big question.

Dr Small

---

### Post by r4ik on 2007-02-12
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

Good luck !

---

### Post by kaptainlange on 2007-02-12
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

That link should give you a good summary of what repositories to add.  Also, that same page includes a section on adding dvd playback, so give it a view if you're still having difficulty.

Drat r4ik beat me.

---

### Post by Maestro23 on 2007-02-12
> **Dr Small said:**
> Well yeah, I basically had an understanding of that much, but WHAT to put in the /etc/apt/sources.list is the big question.

Dr Small

The "http://medibuntu...." is what you add to your sources.list depending on your version of Ubuntu.

Didn't see you were using Dapper. Dapper help link: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

---

### Post by Dr Small on 2007-02-12
Thank-you! Thank-you! It works now.
And, for the record of me having to ever have to do this again, or for someone else,
I went to the page submitted by r4ik (because his was Ubuntu Dapper page) and found:

```
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ dapper free non-free
deb-src http://medibuntu.sos-sts.com/repo/ dapper free non-free
```

Pasted that into my /etc/app/sources.list, ran sudo apt-get update
Then went to the Synaptic and installed libdvdcss2 (which I could have done by sudo apt-get install libdvdcss2 )
But, now my dvd works, and I am very grateful to the people at Ubuntu Forums! :)

Dr Small

---

### Post by mb125 on 2007-12-05
anyone have any luck installing in libdvdcss2 in gutsy?

---

### Post by iris-n on 2007-12-06
I did, and it's working perfectly. Try using this guide: 
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Or if you just want to install it, and runs a i386 you cant use this:
```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```

---

### Post by nikoPSK on 2007-12-06
here you go:

add the medibuntu repos:

```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

```

that'll add the repos to your sources.list file, now:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Install all your requirements:

```
sudo apt-get install libdvdread3 libdvdcss2 libxine1-ffmpeg totem-xine
```

It'll change totem gstreamer to totem xine to enable dvd menus. (if in  gutsy replace  the  section of the top code 'fiesty" to "gutsy".

Hope that helps,
Niko

---

### Post by mb125 on 2007-12-06
OK i got it all installed now, thanks guy's

---

### Post by nikoPSK on 2007-12-06
np:popcorn:

---

### Post by stchman on 2007-12-06
> **Dr Small said:**
> Hello, I have been trying to install libdvdcss2 but without success from here:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)



I can't figure out how to add the repository. Could anyone give me some insight?

Dr Small

Here is a tutorial on getting your Ubuntu install to play encrypted DVDs.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

