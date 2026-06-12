---
title: "Weird error when updating"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by zaxer on 2005-12-16
Hello guys!

Im getting this error when executing apt-get update. Can you help me?

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Thanks!

---

### Post by NotJustANewbie on 2005-12-17
This is to do with the GPG signature which "validate" that the list is genuine. Go to your update manager and select authentication. You will see some options to do with the signatures. Click restore defaults.

---

### Post by zaxer on 2005-12-17
[QUOTE=NotJustANewbie]This is to do with the GPG signature which "validate" that the list is genuine. Go to your update manager and select authentication. You will see some options to do with the signatures. Click restore defaults.[/QUOTE]

Ive already tried that, but the error is still there :(

---

### Post by bb002 on 2005-12-19
apt-get is goofing up and not redownloading a repository list to fix the error. I got this every once in a while in Hoary but not since I updated to breezy. My fix requires root priviledges but as long as you enter my commands exactly everything should work just fine. I'm not responsible for any kind of damage that may result. Nothing should happen but just incase.

Open a terminal and enter the following: (make sure apt-get and synaptic are not running.)
```

sudo rm /var/lib/apt/lists/security.ubuntu.com_dists_breezy-security_Release
sudo rm /var/lib/apt/lists/security.ubuntu.com_dists_breezy-security_Release.gpg
sudo apt-get update

```
The above makes apt-get redownload only the list that was causing the error and make that error go away.


If the above didn't work try the following, it will force apt-get (or synaptic) to redownload all repository lists. Including those on the cd so insert your breezy install cd before running the last command, "sudo apt-get update". This is the method that I originally created and used for when I had this error.
Open up a terminal and enter: (make sure apt-get and synaptic are not running.)
```

cd /var/lib/apt/
sudo mv ./lists ./lists.bad
sudo mkdir ./lists ./lists/partial
sudo apt-get update

```

---

### Post by psypher on 2005-12-28
Hi I am also getting that problem and I have tried both your methods and still have a problem, here is my errors:

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

---

### Post by PhilOSparta on 2006-02-10
There is an error in the GPG key in your box compared to the one at the source site.   I ran [http://ubuntulinux.nl/source-o-matic]("http://ubuntulinux.nl/source-o-matic")
 which generates a sources.list file for you based on the repos that you want.  Under sudo, replace your /etc/apt/sources.list file with the generated file.  The generated file has instructions in it for changing the keys for the repos.

This is a sample of the file generated for one of my selected repos.
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

Check the man page for apt-key for additional info.

This worked for me.

---

### Post by Terry of Astoria on 2006-02-10
I just installed breezy as a server - no gui. 
When I apt-get update I get a different error. Here it is.
```
W: GPG error: http://security.ubuntu.com breezy-security Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com breezy Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com breezy-updates Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems

``` 
I tried the above suggestions. They didn't help. Hm....

---

### Post by chettyk on 2006-02-12
[QUOTE=bb002]
If the above didn't work try the following, it will force apt-get (or synaptic) to redownload all repository lists. Including those on the cd so insert your breezy install cd before running the last command, "sudo apt-get update". This is the method that I originally created and used for when I had this error.
Open up a terminal and enter: (make sure apt-get and synaptic are not running.)
```

cd /var/lib/apt/
sudo mv ./lists ./lists.bad
sudo mkdir ./lists ./lists/partial
sudo apt-get update

```[/QUOTE]

Well, this worked fine for me. In addition, I had to run
```
sudo apt-cdrom add
```
so that the files were in the Ubuntu installation CD were also included.

---

### Post by emperor on 2006-02-12
I found the following partial key was causing he problem.
Deleting this key and then doing a synaptic reload resolved the problem.

root@i9300:/var/lib/apt/lists/partial# dir
security.ubuntu.com_ubuntu_dists_breezy-security_Release.gpg

---

### Post by AgenT on 2006-02-12
If you have the correct GPG key and are still having problems this **fix** should help.

There's some weird glitch where residual info hangs out and gives you a GPG signature error. If that's the case, do this: 
Back up the sources.list with this command: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup 
``` Then edit the sources.list by typing ```
sudo gedit /etc/apt/sources.list
``` and delete everything. 
```
 sudo apt-get update 
```with your empty repositories list. 
Finally, ```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
``` ```
sudo apt-get update
``` [Source]("http://www.psychocats.net/linux/sources.php")

---

