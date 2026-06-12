---
title: "Updates error"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by mlocsin on 2007-03-04
Hi, I just installed 6.06.1 LTS. When I run Update Manager I get the following errors:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu7_i386.deb)
  Connection failed [IP: 91.189.89.8 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/langpack-locales/locales_2.3.18.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/langpack-locales/locales_2.3.18.1_all.deb)
  Connection failed [IP: 91.189.89.8 80]

...

And so on for 18 packages. Pings to the IP respond fine with ~105ms response time. When I open the URLs in Firefox they all exist (and I'm prompted to open the files with the GDebi package installer -- which I don't want to do).

Am I doing something wrong? My internet connection is fine -- I'm posting this message from the system I just built. Any help would be greatly appreciated.

---

### Post by chggr on 2007-03-04
Same problems have been reported in the past. Try searching the forum to find a solution to your problem.

One solution can be the following.
Edit the file /etc/apt/sources.list (after you back it up) and change http to ftp.

---

### Post by mlocsin on 2007-03-05
Ok. Problem solved. For any other newbies out there trying out Ubuntu for the first time and installing 6.06 LTS, you'll get the same errors and won't be able to access the repositories -- ergo, NO UPDATES! :mad:

For us newbies, here's the (GUI-based) solution:

1. Open System -> Administration -> Synaptic Package Manager -> Settings -> Repositories

2. Highlight each channel and click on the "- Remove" button to remove them all. Don't worry -- none of them are working, anyways*.

3. Click on "- Add" -> Custom and copy/paste each one of the four lines below into the APT line field. Click on "Add Channel" to add. (note: these URIs where retrieved from [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/))

deb [ftp://us.archive.ubuntu.com/ubuntu](ftp://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [ftp://us.archive.ubuntu.com/ubuntu](ftp://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) dapper-security universe multiverse

4. Close Synaptic Package Manager.

5. [optional] Open System -> Administration -> Update Manager and check for Software Updates.


* Because someone decided to turn off http downloading on the servers. I know this is what happened because my 6.06 system on VMWare (which I set up 4 months ago and I hadn't used in a while) used to receive updates daily -- and it came up with the same errors when I ran Update Manager.

BTW, somebody should send a note to Ubuntu that NONE of the existing 6.06 users will receive updates -- including SECURITY updates -- until they do this. And the kicker is -- THEY DON'T KNOW IT! ](*,) 

This makes even M$ look good. :mad:

---

