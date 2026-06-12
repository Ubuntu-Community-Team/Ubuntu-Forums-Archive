---
title: "Vmware tools install"
date: 2008-02-28
forum: Apple Intel Users
---

### Post by OCTOG3N on 2008-02-28
Hi, I have a 20" aluminum iMac and am using the vmware trial to test drive Ubuntu (I've played with it before on PCs) ubuntu is running great under vmware but in order to get better graphics and more interoperability between osx and ubuntu I wanted to install the vmware tools package. I've looked at several tutorials but when I select Virtual Machine, install vmware tools, the mounted cd is just full of text files with no packages to speak of. Can someone help me? I'm sure I installed ubuntu properly under vmware and it's working great.

---

### Post by cyberdork33 on 2008-02-28
there should be an archive file and an rpm file. The archive has the source code for the tools that needs to be used.

---

### Post by OCTOG3N on 2008-02-29
> **cyberdork33 said:**
> there should be an archive file and an rpm file. The archive has the source code for the tools that needs to be used.yes I know, but that is not what I get. when I mount the vmware tools it is just full of incomprehensible text files.

[IMG]http://i71.photobucket.com/albums/i128/octolink_64/Ubuntuissue.png[/IMG]

---

### Post by cyberdork33 on 2008-02-29
I don't know what to tell you then. A bug maybe. The file names look like code, and that is definitely not right. Are you using a Beta version or something? You might ask in the [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") forum, they may have seen that before...

---

### Post by kathy4scuba2 on 2008-03-13
I ran into the same problem.  I ejected the DVD (image) in the File browser, then did a "virtual machine...cancel install...".  I then did an install virtual machine again.  I did this a couple of times and it finally came up correctly.  Not sure what was going on.  After struggling for a while, I finally opened a shell window,  and did a

tar -xzvf  <path to DVD>/vmware-tools-distrib.tar.gz  (I'm not sure of the exact name).
cd <directory>
./vmware-install.pl

Hope this helps.

---

### Post by buzzsawddog on 2008-03-15
First off you need to:

    sudo apt-get install build-essential
    sudo apt-get install linux-headers-`uname -r`

after you have done that mount the cd then do:

    cp /cdrom/*.gz /tmp/
    cd /tmp
    tar xvzf VM*.gz
    cd vmware*
    sudo ./vmware-install.pl

you can select the defaults, then restart the VM and life is good :-)

---

### Post by bronkeydain on 2008-03-17
I had the same problem, what I did is upload the packages to an ftp server, and then download them again to the virtual machine. Not a fix, just a dirty work around.... :)

---

