---
title: "I want to use Ubuntu and stop using Windows but..."
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by lorenafavario on 2007-08-27
Hello:

My name is Lorena and Im from Argentina.
I got Ubuntu 7.04 and run it as a live cd.
It was able to see my old photo camera (Polaroid Fun Flash 640 - parallel port) **but it was not able to detect my old scanner (Genius Color Page Vivid III V2 - parallel port too).**I went to SANE website and it is in the list but the scanner is not found.
What can I do?

**Is important for you to know that I dont have any kind of internet connection at home, so I need to be able to get the programs, plug ins, etc from the cyber caffe (10 blocks from home). And all the computers there run with windows.**
At the same time I would like to be able to listen to my mp3s, view my dvds (I rent them close to home) and my collected videos and photos that have different formats (all of them so common in windows).

I was reading about downloading packages, burning a CD and use it as a repository (I would like to be able to surf those repositories and select the programs I want for my Ubuntu).

I need somebody to explain me in easy words what to do!!!

Thanks for all your help in advance
Best regards Lorena

---

### Post by sumguy231 on 2007-08-27
Honestly, if you have the cash it might be more worth it to buy a different scanner which is already compatible; You can find a list of scanners and how compatible they are with various Linux distributions here:
[http://www.linuxquestions.org/hcl/index.php/cat/199](http://www.linuxquestions.org/hcl/index.php/cat/199)

Also, there's a short list specifically for Ubuntu here:
[https://wiki.ubuntu.com/HardwareSupportComponentsScanners](https://wiki.ubuntu.com/HardwareSupportComponentsScanners)

---

### Post by por100pre1 on 2007-08-27
Honestamente creo que la mejor solucion es la de mover fisicamente la PC a una ubicacion con internet porque los codecs de mp3, dvd, etc deben ser descargados, no estan presentes en los CDs de Ubuntu. Trata de llevar este asunto a los Ubunteros Argentinos a ver si te pueden ayudar... :(

---

### Post by sumguy231 on 2007-08-27
I agree with the above, unfortunately. Ubuntu is much more usable with an Internet connection and it will be difficult to keep it current and configured without one. I did forget to mention that you can download files manually from packages.ubuntu.org for use on your computer. There is also the excellent apt on cd, but it only works if you know someone with a computer with Ubuntu or Debian and an internet connection.

---

### Post by logos34 on 2007-08-27
Get the [4 GB DVD for 7.04 Feisty (ubuntu-7.04-dvd-i386.iso)]("ubuntu-7.04-dvd-i386.iso")--it'll limit the amount of packages you'll need to add.  For those not included on the disc your most viable option is probably to manually download from the archive mentioned above (actually it's [http://packages.ubuntu.com/](http://packages.ubuntu.com/)).  There's a [list file here ]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/feisty/release/ubuntu-7.04-dvd-i386.list")of everything included on the DVD.  

This, of course, assumes you have a dvdrom/dvd-rw, and a way to either burn the downloaded iso to disc before you take it home, or a USB stick or memory card large enough  to carry it on (EDIT: or just purchase it [here]("http://www.amazon.com/gp/redirect.html?ie=UTF8&location=http%3A%2F%2Fwww.amazon.com%2FCanonical-Ubuntu-7-04-PC-Edition%2Fdp%2FB000PSWZSC%3Fie%3DUTF8%26s%3Dsoftware%26qid%3D1177942094%26sr%3D1-2&tag=ubuntushipit-20&linkCode=ur2&camp=1789&creative=9325").)

Alternatively, I highly recommend [Linux Mint]("http://en.wikipedia.org/wiki/Linux_Mint") (CD-size only -- no large DVD version) in light of your special situation and need for multimedia support--it's got all the av codecs and players already installed...so you shouldn't have to download much...should play just about any format out of the box (except maybe libdvdcss2 for commercial dvd movie playback.  Not sure).  Linux Mint shares the same repositories as ubuntu so I think you could even use it with the DVD as a software source.

Not sure about how to get that scanner working, though

Best of luck

---

### Post by Rotaj on 2007-08-27
This may seem like an odd choice, but have you tried Kurumin? It has excellent hardware detection, and seems like avery nice distro.  It is in Portugese.

---

### Post by charly gr on 2007-08-31
Lorena, I left you an answer in the the argentine forum,  here is a link I think you should find useful:

[http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html](http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html)


saludos!

[www.diariodeunviajeamisiones.blogspot.com](www.diariodeunviajeamisiones.blogspot.com)

---

### Post by lorenafavario on 2007-09-03
Hi everybody:

Thanks for all your help, my computer is working great, no more windows!!!!!
I can watch my dvds, videos and listen to my mp3s.
My old photo camera is working fine, Im so happy I could cry!!!!
BUT....
My old scanner (parallel port) doesnt want to work GGGGGRRRRR!!!!:mad:
I already installed with synaptic libsane extras but Ihave to edit a file:  
**Edit  the /etc/sane.d/dll.conf and enable the right driver for your scanner**
How can I do this???? I have to use sudo in the terminal to get privileges but then what?????
Im in troubles here and this is the last thing I have to do for my computer to completly work.
A big hug from Argentina and I will be waiting for your advices and answers. All of them are going to be very welcome.
Lorena

---

### Post by Empath on 2007-09-03
You can edit the file by doing the following:

Click Applications
Click Accessories
Click Terminal

Type in sudo gedit /etc/sane.d/dll.conf
It'll ask for your password. Then the file you need to edit will come up.

---

### Post by lorenafavario on 2007-09-05
Hello there!

Well I used gedit to edit the .conf file for the backend of my scanner and I followed all the steps and advices in the mans files but Ubuntu still doesnt see my scanner.
And another issue Im having is that I cant change the monitor configurationto 1280 x 1024 (or something like that).
What can I do now guys?
Thanks for the help in advance
Lorena

---

### Post by Gone fishing on 2007-09-05
Yes, you want an internet connection with Ubuntu - however, it will be a useful too without one once it is setup. You will be able to watch DVDs, play music, word process share files etc 

Windows without an internet connection MS Windows is a disaster. Without an up to date AV your PC will soon become infested with viruses and infect all who you share files with. Your PC will slow down and become something vile and unpleasant.  

I would recommend  Linux, BeOS, SkyOS, RiSC OS or just about anything over Windows to a person with out an internet connection.

---

### Post by Empath on 2007-09-05
For the resolution issue, did you enable the restricted drivers for your ati/nvidia video card assuming you have one?

---

