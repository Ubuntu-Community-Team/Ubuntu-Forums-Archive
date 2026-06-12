---
title: "enable flash in 64 bit firefox"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by rajeev1204 on 2006-12-24
hi


(i have posted this here and in 64 bit users section cos this is a widely read section for beginners . i request mods please dont move it.)

nspluginwrapper works beautifully with flash 7( and flash 9 beta 2) so u can watch ur favourite youtube clips.

Download flash from adobe before doing this.


Here is the link for step by step install for our systems

[http://plugindoc.mozdev.org/linux-amd64.html](http://plugindoc.mozdev.org/linux-amd64.html)

follow it completely and u r good to go!

important is to download both player and viewer ,also remember to use /usr/lib/mozilla-firefox/plugins as the path cos that is where our 64 bit firefox is located for the final step of installing nspluginwrapper   .

you will need the alien package to convert the rpm to debs .but that is available in repos. So for all those who had issues installing in the past with imcomplete instructions ( me included), this link will solve it.


regards


rajeev

---

### Post by encikraju on 2007-01-05
Hi, I've got a question. What do you mean by changing the /usr/lib/mozilla....
Should i replace it into this code?
sudo ln -s /usr/lib/nspluginwrapper/x86_64/npconfig /usr/bin/nspluginwrapper

---

### Post by rajeev1204 on 2007-01-05
hi

no no

 After u have completed those 4 steps , u need to install nspluginwrapper in ur browser directory  like this 

nspluginwrapper -i /usr/lib/mozilla-firefox/plugins/libflashplayer.so


let me know


regards

rajeev

---

### Post by encikraju on 2007-01-05
Thanks for reply.
I did all those 4 steps + nspluginwrapper -i /usr/lib/mozilla-firefox/plugins/libflashplayer.so but mozilla still crash when visiting website with flash plugin.
Any idea?

---

### Post by rajeev1204 on 2007-01-05
hmm


 u need to remove **libflash-mozplugin **from the repos.

Which version of ubuntu r u using? edgy?

which version of flash ?  u need flash beta 2 

Guaranteed to work now:)

---

### Post by souleestyles on 2007-01-06
hi all,

I set up ubuntu 6.10 64 bits today and for about 4 hours, even more i try to install flash. I followed the topic but when i run this command :

[CODE][:~$ nspluginwrapper -i /usr/lib/mozilla-firefox/plugins/libflashplayer.so/CODE]

here the error i have :

[CODE]nspluginwrapper: /usr/lib/mozilla-firefox/plugins/libflashplayer.so is not a valid NPAPI plugin[/CODE

Does anyone have an idea about this error ?

thanks in advance

---

### Post by encikraju on 2007-01-08
Hi, I'm using edgy. 
It seems half work. Firefox doesnt crash anymore
but I still can't listen to the song(Myspace).
WHy?

---

### Post by laloch on 2007-01-17
souleestyles: nspluginwrapper requires ia32-libs, ia32-libs-gtk and linux32 packages. check if you have them installed. make shure that you DON'T have libswfdec library. also, in order for flash player to play sound, you have to install lib32asound2 package. then
```
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
/etc/init.d/alsa-utils restart
```
restart firefox and you are ready to go.

---

### Post by ndefontenay on 2007-03-28
i've checked and I got the libswfdec library.

Locate libswfdec gives me this:
```

/var/cache/apt/archives/libswfdec0.3_0.3.6-2ubuntu2_amd64.deb
/var/lib/dpkg/info/libswfdec0.3.shlibs
/var/lib/dpkg/info/libswfdec0.3.list
/var/lib/dpkg/info/libswfdec0.3.postinst
/var/lib/dpkg/info/libswfdec0.3.postrm
/var/lib/dpkg/info/libswfdec0.3.md5sums
/usr/lib/libswfdec-0.3.so.0.0.0
/usr/lib/libswfdec-0.3.so.0
/usr/share/doc/libswfdec0.3
/usr/share/doc/libswfdec0.3/copyright
/usr/share/doc/libswfdec0.3/README
/usr/share/doc/libswfdec0.3/TODO
/usr/share/doc/libswfdec0.3/AUTHORS
/usr/share/doc/libswfdec0.3/changelog.Debian.gz
/usr/share/doc/libswfdec0.3/changelog.gz
/usr/share/doc/libswfdec0.3/NEWS.gz
```

how do I get rid of it?

Thanks for your help.

---

### Post by ndefontenay on 2007-03-28
Ok.

I got flashplayer 9 working with firefox32.

I had installed 7.0 previously.
What I did is simply to untar flashplayer90
and copy libflashplayer.so to the following directory

/usr/lib32/firefox32/plugins/

(I backed up the previous one just in case)

flashplayer 9.0 works like a charm.

---

### Post by rajeev1204 on 2007-04-03
Hi

I have a small update .

For all those having the error .... This is not a valid NPAPI plugin 

The final step of installing nspluginwrapper should be done with sudo
Like this  ----  sudo nspluginwrapper  -i  /usr/lib/firefox/plugins/libflashplayer.so .

Basically just run all instructions with sudo.

I am running flash in feisty now  :guitar: 


regards

rajeev

---

