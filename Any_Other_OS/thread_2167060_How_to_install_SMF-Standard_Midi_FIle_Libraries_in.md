---
title: "How to install SMF-Standard Midi FIle Libraries in Fedora 19?"
date: 2013-08-12
forum: Any Other OS
---

### Post by su:bhatta on 2013-08-12
How to install 'libsmf-dev' in Fedora? I am installing LinuxBand in Fedora Spin Jam and one of the dependencies is libsmf-dev. Here is some details :

Now , i understand that in debian/Ubuntu I merely need to do 'apt-get install libsmf-dev' ( I am running Linuxband sucessfully in UbuntuStudio 13.04)

But doing 'yum install libsmf-dev' doesn't do it! If i am not mistaken 'smf' may be in the Fedora libraries in some other name !

EG. another dependency 'libjack-dev' was under the name 'jack-audio-connection-kit-devel'

How do i find out 'libsmf-dev' and install it....? i've tried out  'smf-devel',  'libsmf-devel', standard-midi-file-devel',  'standard-midi-fileformat-devel' et al !

Last thing I did was down load from LibSMF their 1.36 version file &  do a './configure, make & Make install' that also, Failed !  Website: Standard MIDI File format library
[http://sourceforge.net/projects/libsmf](http://sourceforge.net/projects/libsmf)

From apper I've been able to Get the Python-GTKSourceview Bit too... so, If I am not mistaken SMF is the last hurdle !

Any help is much appreciated!

---

### Post by su:bhatta on 2013-08-16
Ok, I am closing the post coz, I got an reply in ask.fedoraproject that libsmf is not available in Fedora yet, at least in repos, and I have to compile it!

Now, I dont know what to do, compile libsmf first & then libsmf-devel, On top of that how to do it in /usr and not/usr/ local !!!!

Not using Fedora Jam anymore.....

---

