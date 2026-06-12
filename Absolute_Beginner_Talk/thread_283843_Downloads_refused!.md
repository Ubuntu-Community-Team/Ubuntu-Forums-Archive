---
title: "Downloads refused!"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-10-24
Whenever I try to download any software, I get something like this:

[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg:](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://www.getautomatix.com/apt/dists/dapper/Release.gpg:](http://www.getautomatix.com/apt/dists/dapper/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://dl.google.com/linux/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/deb/dists/stable/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://wine.budgetdedicated.com/apt/dists/dapper/Release.gpg:](http://wine.budgetdedicated.com/apt/dists/dapper/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by meng on 2006-10-24
I wonder if you could have the same problem described here:
[http://ubuntuforums.org/showthread.php?t=268792](http://ubuntuforums.org/showthread.php?t=268792)
Let us know.

---

### Post by OptimusPrime on 2006-10-24
I think I have the same problem, but what is the annon proxy, and how do I uninstall it?

---

### Post by meng on 2006-10-24
According to packages.ubuntu.com, anon-proxy allows you to surf the web anonymously. You would uninstall it by:
sudo apt-get remove anon-proxy

---

### Post by OptimusPrime on 2006-10-24
Well, I uninstalled it, and I get this when I try to download something:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/c/cd-discid/cd-discid_0.9-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/c/cd-discid/cd-discid_0.9-1_amd64.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/v/vorbis-tools/vorbis-tools_1.1.1-3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/v/vorbis-tools/vorbis-tools_1.1.1-3_amd64.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/lame_3.96.1-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/lame_3.96.1-1_amd64.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/a/abcde/abcde_2.3.99.2-1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/abcde/abcde_2.3.99.2-1_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/f/ffmpeg/ffmpeg_0.cvs20050918-5ubuntu1.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/f/ffmpeg/ffmpeg_0.cvs20050918-5ubuntu1.1_amd64.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-flac_0.8.12-1ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-flac_0.8.12-1ubuntu2_amd64.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-gnomevfs_0.8.12-1ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-gnomevfs_0.8.12-1ubuntu2_amd64.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/n/nautilus-script-manager/nautilus-script-manager_0.0.5-0ubuntu3_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/n/nautilus-script-manager/nautilus-script-manager_0.0.5-0ubuntu3_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/a/audio-convert/nautilus-script-audio-convert_0.3.1.1-0ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/audio-convert/nautilus-script-audio-convert_0.3.1.1-0ubuntu2_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-python/python-gst_0.8.3-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-python/python-gst_0.8.3-1_amd64.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/s/soundconverter/soundconverter_0.8.3-0ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/s/soundconverter/soundconverter_0.8.3-0ubuntu2_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/s/soundkonverter/soundkonverter_0.1.99+0.2beta2-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/soundkonverter/soundkonverter_0.1.99+0.2beta2-0ubuntu1_amd64.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by brash on 2006-10-24
Maybe try a reboot after uninstalling?

---

### Post by meng on 2006-10-24
Well obviously there was some change, because the message is different! Unless someone else offers a suggestion in the next 5 minutes, would you like to reboot your computer and try again? I know it's not the Linux way of doing things (usually a reboot is not required) but it can't hurt ...

---

### Post by OptimusPrime on 2006-10-24
I don't know, and nobody seems to know either.  I think I need some kind of Linux God or something.

---

### Post by OptimusPrime on 2006-10-24
I have been having problems with downloads ever since I installed Linux.  EACH time I install (or uninstall) something new, I get this at the end of the installation:
E: liblog4j1.2-java-doc: subprocess post-installation script returned error exit status 2
E: clvm: subprocess post-installation script returned error exit status 3

---

### Post by meng on 2006-10-24
I'm pretty sure I've seen that described as an automatix problem. Have you tried the forums at getautomatix? (for both of those problems)

---

### Post by OptimusPrime on 2006-10-24
I have not, you think they could help.

---

### Post by OptimusPrime on 2006-10-24
Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main automatix2 1.0-1.3-6.06dapper1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/main/binary-amd64/automatix2_1.0-1.3-6.06dapper1_amd64.deb](http://www.getautomatix.com/apt/dists/dapper/main/binary-amd64/automatix2_1.0-1.3-6.06dapper1_amd64.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
wesley@wesley-laptop:~$

---

### Post by OptimusPrime on 2006-10-24
I need to install software to fix my problem, but I can't install software, so am I doomed?

---

### Post by meng on 2006-10-24
> **OptimusPrime said:**
> I have not, you think they could help.
I'm not sure, but as I said I _thought_ I saw the same problem attributed to Automatix. I cannot find any such threads on searching these forums now. At any rate it is clear that you have been waiting patiently for a solution here (2 weeks?) and no one has come up with the answer yet.

---

### Post by arnieboy on 2006-10-25
Automatix does not deal with proxies or install annon-proxy. 
It would be nice of you (meng) to clarify with us before calling anything an Automatix problem and confusing users.

---

