---
title: "Updating graphics driver"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by shammoon on 2007-10-19
Hello,

My first post as a noob in this forum. I have used MS products all my life, trying to get into Linux now ;) so bear with me if I don't know the basics..

I have a amd 64 4200x2 machine with 2 gig ram, Vista 64 business and an NVIDIA 7300. I installed Ubuntu 7,10 for the first time as a dual boot with vista. Seems all ok except for an occasional freezing. I have a feeling this happens when I try to use the graphics capabilities. For example If I click on the show desktop button it will freeze.

I am not sure but I guess it has to do with the drivers of the graphics card. so I am trying to install the latest drivers. downloaded them and double clicked and it asks me to run as root... how do I do this?

sorry if it is very simple...

---

### Post by corowakid on 2007-10-19
I'd suggest before you go any further that you look at this site:

[http://albertomilone.com](http://albertomilone.com)

He's the definitive guy for installing nVidia drivers - has always worked for me. His site allows you to download and print any suggestions you might want. Well worth going thru before you start with xconf files and the like.

---

### Post by Sir_Sid on 2007-10-19
what type of file is it?

To run it as root, you have to open terminal and navigate to your desktop. You can type in the command 
```
ls
```
to display whats in your folder. You use the command
```
cd
```
to change directory. For example if I wanted to go to my desktop I would type this in (starting from my home directory) 

```
cd Desktop
```

Navigate to the folder which contains your file and then do 
> sudo FILENAME
type in your password at the prompt and it will run the program as root. 

The cheater way of doing it is just typing sudo and then dragging the file into the terminal. That will paste the location of the file into the terminal. 

Remember its case sensitive.


edit

If you are messing with graphics drivers, Definitely check out that above site.

---

### Post by Hospadar on 2007-10-19
you shouldn't use the downloaded drivers really.  If you've already installed them and gotten them working, then just leave em, but if you have yet to try to install them properly, go to System->Administration->Restricted Drivers Manager and enable the restricted nvidia driver there.  Alternatively you could manually install the "nvidia-glx" and activate it with the command in the package description ("sudo nvidia-glx config" or something like that)

If you've already attempted to install the ones from nvidia's website, I would use the envy script suggested above as you need to clean out a couple kernel module files and it's not a good idea to do this manually if you don't know what's up. (that's the script suggested at [http://albertomilone.com]("http://albertomilone.com/"))

---

### Post by shammoon on 2007-10-19
> **Hospadar said:**
> you shouldn't use the downloaded drivers really.  If you've already installed them and gotten them working, then just leave em, but if you have yet to try to install them properly, go to System->Administration->Restricted Drivers Manager and enable the restricted nvidia driver there...

corowakid, Sir_Sid and Hospadar

thank you for all your input. I followed Hospadar's advise and enabled the restricted nvidia drivers. This seems to have stabalised the system, I tried a few graphical apps, and also the show desktop button that previously used to freeze ubuntu all together.

I'll keep an eye on it for some time to see if it happens again. I will also check out the website suggested by corowakid: [http://albertomilone.com](http://albertomilone.com) for future refernce.

and finally thank you Sir_Sid for the advise on how to navigate the terminal.

I appreciate all your help, I have to say the first impression of linux/ubuntu and you guys at the forum is pretty sweet!

Thanks again

---

