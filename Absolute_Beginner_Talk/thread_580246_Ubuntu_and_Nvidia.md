---
title: "Ubuntu and Nvidia"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-10-18
Can anyone out there tell me how to get Nvidia GeForce go 7300 to work in ubuntu? (it is a laptop) tried everything, and starting to give up :(

And when i try to install stuff in FireFox (have not tried Add/remove programs yet) i get this
[[img]http://bildr.no/thumb/113623.jpeg[/img]](http://bildr.no/view/113623)

---

### Post by kindafunnylookin on 2007-10-18
go to this link[ http://http://www.psychocats.net/ubuntu/nvidia]("http://http//www.psychocats.net/ubuntu/nvidia")

---

### Post by ajmannen on 2007-10-18
that link only brought me to a weird search site

---

### Post by Pumalite on 2007-10-18
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by BOZG on 2007-10-18
> **ajmannen said:**
> that link only brought me to a weird search site

That's the proper link:
[http://www.psychocats.net/ubuntu/nvidia]("http://www.psychocats.net/ubuntu/nvidia")

If that fails, try getting Envy and using that to configure:
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by buntunub on 2007-10-18
No need for that. Read the Ubuntu Documentation and Community docs. Its all in there with a very simple and fast search

---

### Post by BOZG on 2007-10-18
As for the Firefox issue, go to System>Administration>Software Sources>Ubuntu Software and make sure that all the boxes have a tick and if not, change them to a tick.  Try installing again.

---

### Post by NeBiRuSs on 2007-10-18
Hey to i hope this can help you about install nvidia drivers [Ubuntu Forums]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

And about the error msg from FireFox 

First you need to edit the /etc/apt/sources.list file

**sudo gedit /etc/apt/sources.list**

add the following Repository list and save the file

[B]deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0
deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0[/B]

Now you need to copy the key for this Repository list using the following

**sudo wget [http://3v1n0.tuxfamily.org/EDD1E155.gpg](http://3v1n0.tuxfamily.org/EDD1E155.gpg) -O- | sudo apt-key add -**

Update the source list using the following command

**sudo apt-get update**

Install flash player Plugin using the follwoing command

**sudo apt-get install flashplugin-nonfree**

thats it

---

### Post by ajmannen on 2007-10-19
After i enabled the surces it installed my nvidia card auto installed :)

---

### Post by bhaumik_thacker on 2008-02-15
hello,

now i tried downloading the NVIDIA drivers for ubuntu 7.10 gutsy gibson.
i tired it from both the web-sites:
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)
and
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
but there were some errors which i m unable to understand  :confused:
sending the screen shots and keenly waitning for the reply
thanks.

---

### Post by PmDematagoda on 2008-02-15
Open Software Sources in System>Administration>Software Sources and enable all the choices in the Ubuntu Software tab except for the CD-ROM, after that is done, close the window, you will be asked to reload the sources list, do that, after that is finished you should be able to install the Nvidia driver simply through the Restricted Drivers Manager.

---

### Post by Ex-windows on 2008-02-16
As for the software( nvidia ) issue, did you go to Applications.Software sorces and check all boxes ? If they are not checked do that and try again?  I cant offer any help with envy  as I have never tried it, and not sure what you  need to do about the dependency issue. I am sure someone can offer some insight theere..
Good luck

---

### Post by Scut_Farkus on 2008-02-16
> **PmDematagoda said:**
> Open Software Sources in System>Administration>Software Sources and enable all the choices in the Ubuntu Software tab except for the CD-ROM, after that is done, close the window, you will be asked to reload the sources list, do that, after that is finished you should be able to install the Nvidia driver simply through the Restricted Drivers Manager.

This is EXACTLY what I did and it worked perfectly.  

Good luck!

---

### Post by erginemr on 2008-02-16
> **bhaumik_thacker said:**
> hello,

now i tried downloading the NVIDIA drivers for ubuntu 7.10 gutsy gibson.
i tired it from both the web-sites:
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)
and
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
but there were some errors which i m unable to understand  :confused:
sending the screen shots and keenly waitning for the reply
thanks.

Please try to enable your restricted driver repository. See:
[http://ubuntuforums.org/showpost.php?p=4341810&postcount=4](http://ubuntuforums.org/showpost.php?p=4341810&postcount=4)

EDIT: Sorry for the 4th edition of the same tip! I didn't notice that there was a second page. Stupid me...

---

