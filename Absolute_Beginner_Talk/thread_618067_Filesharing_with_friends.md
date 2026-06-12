---
title: "Filesharing with friends"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Squizz on 2007-11-20
I'm interested in making files available to some friends without the hassle of having to upload them to my webserver first.

Is it possible to simply put the file into a folder and then either use my normal install as a fileserver or ftp?

Thanks in advance :)

---

### Post by dpar on 2007-11-20
This may be worth a read.....

[http://www.poromenos.org/tutorials/bittorrent](http://www.poromenos.org/tutorials/bittorrent)

---

### Post by siciliancasanova on 2007-11-20
I've never done this but if I'm thinking correctly, they don't need to do anything on their end they should be able to SSH into another box by default.  On your end you would need to set up ssh server so they could tap into it.

someone correct me if i'm wrong please, but as of this moment i'm thinking that's how it's done.

---

### Post by Squizz on 2007-11-20
I had a look at the SSH thing and read a few of the threads on here, but I don't want people logging into my machine - I'd rather it were all done over the internet (like a webserver or an ftp server would do)

I'll try out the torrent later, as it's 7am so nobody's online to try it with, but the tutorial looks good ty :)

---

### Post by gimmic on 2007-11-20
I think you could replace their shell with sftp or the like so that they could only run that to file transfer.

or 

You could also download and install apache to host a web dir, but it's likely that your inbound http(80) is blocked if you're on a residential service. You would need to change the default port and give it to your friends along with your IP.

---

### Post by hyper_ch on 2007-11-20
installing mysecureshell will people allow SCP programs such as winscp on windows but they cannot login to the command line. furthermore they will be restricted to their home directory.

---

