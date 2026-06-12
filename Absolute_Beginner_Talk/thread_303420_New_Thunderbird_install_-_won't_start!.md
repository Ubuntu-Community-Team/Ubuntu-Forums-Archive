---
title: "New Thunderbird install - won't start!"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by adam_pretty on 2006-11-20
Hi, my 1st post here!

New to Linux + Ubuntu, finally taken the plunge... 

been installing stuff today, all going well apart from Thunderbird, which I need to be able to share email with the windows partition. 
I installed using "sudo apt-get install mozilla-thunderbird" which seemed to go fine, but now when I click on the icon it doesnt work, also typing "sudo mozilla-thunderbird" into the terminal does nothing at all.

Any help much appreciated!!

Thanks
A.

---

### Post by ewl1217 on 2006-11-20
Try running "mozilla-thunderbird" (without the quotes) from a terminal. Post any error messages or any other output you receive here.

---

### Post by adam_pretty on 2006-11-20
I get nothing from that ... is there an error log I can check?

---

### Post by ewl1217 on 2006-11-20
I'm not aware of any error logs... I was hoping it would give some error to help diagnose the problem. I'm not really sure what the problem is.

---

### Post by cledezma on 2006-11-20
I don't know if this helps, but have you tried to install it using Synaptic Package Manager? It worked for me.

---

### Post by adam_pretty on 2006-11-20
Hi, I tried re-installing fromn the synaptic package manager, still nothing :(

strange...

---

### Post by adam_pretty on 2006-11-20
* bump *

---

### Post by rfruth on 2006-11-20
Uninstall Thunderbird and then delete your profile (assuming its backed up or you don't mind starting from scratch) [http://kb.mozillazine.org/Profile_Manager](http://kb.mozillazine.org/Profile_Manager) (APT doesn't touch your profile) then reinstall Thunderbird, any difference ?

---

### Post by adam_pretty on 2006-11-21
Thanks for your reply,

I tried uninstalling, but couldnt find the profile - possibly because there isnt one yet? My profile was exported from windows and sitting on a shared drive waiting to be used... 
I installed again using aptitude but have the same - nothing

](*,)

---

### Post by adam_pretty on 2006-11-21
OK - I tried deleting the thunderbird folder in both /opt and /etc
Reinstalled
Now it cant find it at all - where does the executable go? 

:-k

---

### Post by adam_pretty on 2006-11-21
anyone?

excuse my impatience!! Just looking for more clues, been searching high & low...

Thanks

---

### Post by adam_pretty on 2006-11-22
* bump * 

8-[

---

### Post by rfruth on 2006-11-22
Sounds like Thunderbird is trying to use the Windows profile which is fine except of corse the themes and extensions are different.  Thunderbird will run with no profile what so ever you just get the welcome to Thunderbird now tell Tbird about your POP server (or whatever) so I'd 1st back-up the Windows profile then manually delete all extension and themes and see if Tbird will start, if not delete some more (newsgroups) and try again, alternately you can use the profile manager [http://kb.mozillazine.org/Profile_Manager#Linux](http://kb.mozillazine.org/Profile_Manager#Linux) ... if a Linux ver of Tbird uses a Windows Tbird profile strange things can happen til you figure out what works.

---

### Post by adam_pretty on 2006-11-23
Thanks, but I havent even been able to set up a profile location yet - I dont see how Tbird could know about the old windows profile sitting on my shared partition. As far as I can see it should just be a fresh install, i've tried reinstalling a few times but I havent been able to get it to start once :(

Any further clues much appreciated...

Yours hopefully... using webmail until I can sort this out!

Cheers

---

### Post by adam_pretty on 2006-11-24
* re- bump *

---

### Post by adam.tropics on 2006-11-24
Do you get any output if you try running mozilla-thunderbird from a terminal? I had locale issues and have to start it from a script, which isn't so bad as you can still just point a panel launcher at it. I don't know what locales you have, but try saving 
```

#!/bin/sh
 export LC_TIME=en_GB.utf8 # or whatever you want
 /usr/bin/mozilla-thunderbird $*
```to /home/<username>/scripts/starttbird.sh or whatever, then make the script executable (right click on it, go to permissions), then test it from terminal

```
./starttbird.sh
```see if that works for you. If it does, add a custom launcher to the panel pointing to that script.

---

### Post by adam_pretty on 2006-11-24
I dont seem to have a /usr/bin/mozilla-thunderbird folder! 

Thanks

---

### Post by adam.tropics on 2006-11-24
it's a file not a folder....If it's not there, open synaptic and check it's actually installed.

---

### Post by adam_pretty on 2006-11-24
Ok - yes I do have that file, only its a link to /opt/thunderbird/thunderbird and its broken - i.e. opt/thunderbird/thunderbird doesn't exist.

I've checked synaptics and reinstalled everything thunderbird that seems relevant a few times... should this be putting something in the opt/thunderbird folder?

---

### Post by adam.tropics on 2006-11-24
No, /opt would be where you installed a version outside of synaptic. So the /usr/bin/mozilla-thunderbird should be a shell script. BTW have you tried running it from a terminal....

mozilla-thunderbird

---

### Post by adam_pretty on 2006-11-24
I deleted the broken link, tried reinstalling again.
I found  /usr/bin/mozilla-thunderbird.ubuntu, but when I try and run that from the terminal, I get: 

> run-mozilla.sh: Cannot execute /usr/lib/mozilla-thunderbird/mozilla-thunderbird.ubuntu-bin.


Had a look at run-mozilla.sh to try and chage the file it runs (mozilla-thunderbird.ubuntu-bin doesnt exist but mozilla-thunderbird-bin does) but that is some mad script looks like it uses some environment variables... maybe I need to change an environment var??

I think I prob messed it up to begin with by trying to install from a downloaded tar file, before using aptitude/synaptics.

---

### Post by adam.tropics on 2006-11-24
could you point me to the how to or download you installed before using synaptic.

---

### Post by adam_pretty on 2006-11-24
I downloaded a script from somewhere, cant remember/find the site, but here is the code:

```
#!/bin/sh
echo "Updating repositories list
"
sudo apt-get update
echo "
Making sure libstdc++5 and the old Thunderbird are installed
"
sudo apt-get -y install mozilla-thunderbird libstdc++5
echo "
Backing up old Thunderbird preferences
"
cp -R ~/.mozilla-thunderbird ~/.mozilla-thunderbird_backup
echo "
Creating symlink to new version data-dir ~/.thunderbird
"
ln -s ~/.mozilla-thunderbird ~/.thunderbird
echo "
Changing to home directory
"
cd
echo "
Downloading Thunderbird from the Mozilla site
"
wget -c http://mozilla.mirrors.tds.net/pub/mozilla.org/thunderbird/releases/1.5.0.2/linux-i686/en-US/thunderbird-1.5.0.2.tar.gz
echo "
Unzipping the .tar.gz file
"
sudo tar -C /opt -x -z -f thunderbird-1.5.0.2.tar.gz
echo "
Removing the unzipped .tar.gz
"
rm thunderbird-1.5.tar.gz
echo "
Linking launcher to new Thunderbird
"
sudo dpkg-divert --divert /usr/bin/mozilla-thunderbird.ubuntu --rename /usr/bin/mozilla-thunderbird
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird
sudo ln -s /opt/thunderbird/thunderbird-bin /opt/thunderbird/mozilla-thunderbird-bin
echo "
The new Thunderbird is installed."

```

Cheers

---

### Post by adam.tropics on 2006-11-24
Try this, assumes you already removed folder /opt/thunderbird/ as you said earlier

```
sudo  dpkg-divert --rename --remove /usr/bin/mozilla-thunderbird

rm ~/.thunderbird

```Reinstall Thunderbird (synaptic)

```
mv ~/.mozilla-thunderbird_backup ~/.mozilla-thunderbird

rm ~/.thunderbird

```

---

### Post by adam_pretty on 2006-11-27
Thanks!

That works now... didnt have to do the last bit, checked it after the install and its all cool now.

Cheers

---

