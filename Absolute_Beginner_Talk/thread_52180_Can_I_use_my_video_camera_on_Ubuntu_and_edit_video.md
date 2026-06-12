---
title: "Can I use my video camera on Ubuntu? and edit video..."
date: 2005-07-26
forum: Absolute Beginner Talk
---

### Post by Wide on 2005-07-26
Howdy all.

I never really played with video editing under Linux, always used it as a work horse for servers, no being I have my wife using Ubuntu on her desktop I would like to use our video camera to play & edit our home movies (not a webcam , Caannon zr-400)

Is this possible?

I did run across Jahshaka, a final cut pro/after effects  look alikethat seems perty nice, my only question is what is the best way to get the cannon zr-400 movies on my Ubunto desktop for my wife to edi.


I really hate when she's right ](*,) 


Any suggestions greatly appreciated

Tim :)

---

### Post by amoser on 2005-07-27
Why yes it is possable to use your video camera with linux.

Just open up synaptic and install Kino (don't forget the Kinoplus package ;)).  And yes, Kino will import the video off of your camera

~Alan

---

### Post by Wide on 2005-07-27
Thank you very much!!

Shes running greatin Kino

Also found a great article on it in Dec 2004 linux journal

Thanks again :)


This sure is a slick distro... \\:D/

---

### Post by spnoe on 2005-08-17
I loaded Kino but run in to a problem i.e. It does not seem to recognise the camera or to be more specific it states " The IEEE 1394 subsystem is not responding.......The raw 1394 must be loaded and you must have read/write permissions.

Has anyone an idea what the hell all that means and how to resolve the issue.
I have afirewire card installed and my camera is a Sony TRV22E.
Help is much appreciated.
Steve

---

### Post by sameat on 2005-08-20
I had the same error until I launched kino as root from a terminal.   This assumes that you have all of the appropriate software bits & pieces loaded,.. you proably do since I am only using a server install of ubuntu plus xfce.  

Now capture is working.  I'm not sure how to get the best quality yet, but I am working on it.

For the record, I am not using the same camera.

Good Luck!

---

### Post by Knyven on 2005-08-21
ahh where did you get KUNO?

im having problems looking for ubuntu softwares, and the ubuntu addon cd link is not working.

---

### Post by xmastree on 2005-08-21
[QUOTE=Knyven]im having problems looking for ubuntu softwares, and the ubuntu addon cd link is not working.[/QUOTE]Forget the addon CD, it's discontinued.
Everything you need should be on the repositories.
[**look here**](http://ubuntuguide.org/#extrarepositories) to see how to access the software, then run synaptic and search for kino.

---

### Post by otherdave on 2006-11-02
> **spnoe said:**
> I loaded Kino but run in to a problem i.e. It does not seem to recognise the camera or to be more specific it states " The IEEE 1394 subsystem is not responding.......The raw 1394 must be loaded and you must have read/write permissions.

Not sure if this will help you, but I saw [this tutorial when I using dvgrab](http://www.braindead.nu/wordpress/index.php?page_id=10) and it mentions some modules that you need to make sure are loaded.

Basically, run:

sudo modprobe dv1394 
sudo modprobe video1394 
sudo modprobe raw1394 
sudo modprobe ohci1394 

to make sure your modules are installed. Maybe that'll fix it?

---

### Post by ubuntu1sttimer on 2007-01-30
Jumping in a bit late but having similar problems with the "raw1394" error message in Kino. 

I tried the above commands with following results.
  
/$ sudo modprobe dv1394
/$ sudo modprobe: command not found
/$ sudo modprobe video1394
/$ sudo modprobe raw1394
/$ sudo modprobe: command not found
/$ sudo modprobe ohci1394
/$ sudo modprobe: command not found

If I understand correctly, only the video1394 module is installed. Is that correct and if so, what do I do now?

Am enjoying Ubuntu Dapper but would like to transfer some of my home video to DVD. Any help will be greatly appreciated.

---

