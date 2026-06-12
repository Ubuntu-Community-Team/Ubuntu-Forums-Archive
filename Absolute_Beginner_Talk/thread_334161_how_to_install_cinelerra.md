---
title: "how to install cinelerra?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by manutdfan2850 on 2007-01-08
i downloaded cinelerra 2.1 from here : [http://heroinewarrior.com/download.php3](http://heroinewarrior.com/download.php3)

but how do I install it??

plz help

thanks

---

### Post by Efwis on 2007-01-08
Make sure you have build-essential installed first, this will have all the software needed to make and compile the program.

open terminal Applications>Accessories>Terminal and do the following
```
sudo aptitude install build-essential
```
then do the following
```
cd /path/to/file
./configure
make
make install
```

You will have to make sure you have all dependencies met.

---

### Post by elettronicha on 2007-01-08
Have you read [this how-to]("http://www.ubuntuforums.org/showthread.php?p=1961508") yet?

---

### Post by manutdfan2850 on 2007-01-08
sorry i am really bad at this stuff so ill need some more help. here is what I did. 

> **Efwis said:**
> Make sure you have build-essential installed first, this will have all the software needed to make and compile the program.


open terminal Applications>Accessories>Terminal and do the following
```
sudo aptitude install build-essential
```

ok i did that

> 
then do the following
```
cd /path/to/file
./configure
make
make install
```

You will have to make sure you have all dependencies met.

this is where i'm confused. Assume I donwloaded the file to the desktop. and the file's name is "cinelerra-2.1-src.tar.bz2"

could you explain it step by step what to type in the terminal to install the program? 

Thanks

---

### Post by manutdfan2850 on 2007-01-08
why is installing this app so conufsing??? can't it be done through synaptic?

---

### Post by Efwis on 2007-01-08
> **manutdfan2850 said:**
> sorry i am really bad at this stuff so ill need some more help. here is what I did. 



ok i did that



this is where i'm confused. Assume I donwloaded the file to the desktop. and the file's name is "cinelerra-2.1-src.tar.bz2"

could you explain it step by step what to type in the terminal to install the program? 

Thanks
just double click on the tar.bz2 file, your archive manager will open up and then you just choose to extract it. the next step would be to open terminal and enter
```
cd /home/username/Desktop/cinelerra-2.1
```
Replace username with the username you use on your system. For example mine would be
```
cd /home/edward/Desktop/cinelerra-2.1
```
Then follow the rest of the steps I outlined perviously.

---

### Post by manutdfan2850 on 2007-01-08
> **Efwis said:**
> just double click on the tar.bz2 file, your archive manager will open up and then you just choose to extract it. the next step would be to open terminal and enter
```
cd /home/username/Desktop/cinelerra-2.1
```
Replace username with the username you use on your system. For example mine would be
```
cd /home/edward/Desktop/cinelerra-2.1
```
Then follow the rest of the steps I outlined perviously.


ok now when i say ./configure i get this message:  

*** Nasm is required.  Download it from nasm.sourceforge.net
 *** Yasm is required.  Download it from [www.tortall.net/projects/yasm/](www.tortall.net/projects/yasm/)


in any case, i found and succusfully installed Cinelerra using directions from this site: [http://flavor8.com/index.php/2006/07/15/mainactor-vs-cinelerra-installing/](http://flavor8.com/index.php/2006/07/15/mainactor-vs-cinelerra-installing/)

Cinelerra

>     * Edit your /etc/apt/sources.list, and add the following repository:
          o deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./
          o deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./
    * On the command line, run the following:
          o sudo apt-get update
          o sudo apt-get install cinelerra


thanks

---

### Post by MetalMusicAddict on 2007-01-08
Cinelerra-CV is currently being worked on for Feisty.

---

### Post by Efwis on 2007-01-08
> **manutdfan2850 said:**
> ok now when i say ./configure i get this message:  

*** Nasm is required.  Download it from nasm.sourceforge.net
 *** Yasm is required.  Download it from [www.tortall.net/projects/yasm/](www.tortall.net/projects/yasm/)


in any case, i found and succusfully installed Cinelerra using directions from this site: [http://flavor8.com/index.php/2006/07/15/mainactor-vs-cinelerra-installing/](http://flavor8.com/index.php/2006/07/15/mainactor-vs-cinelerra-installing/)

Cinelerra



thanks

glad you got it installed. for reference,
the reason you got this section:
> 
*** Nasm is required.  Download it from nasm.sourceforge.net
 *** Yasm is required.  Download it from [www.tortall.net/projects/yasm/](www.tortall.net/projects/yasm/)

it because they are dependencies, without them the program won't work.

---

### Post by TheFlamingBush on 2007-05-29
> **elettronicha said:**
> Have you read [this how-to]("http://www.ubuntuforums.org/showthread.php?p=1961508") yet?


this worked for me....dapper! :)

---

