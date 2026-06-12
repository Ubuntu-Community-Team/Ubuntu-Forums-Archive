---
title: "Synaptic admin rights?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by britonk on 2007-04-06
Can anyone please help me?

I have installed Ubuntu and managed to get it working with my NVidia 7600GT but it's stuck on a 640X480 screen res. I expect this is because I am using the "vesa" driver?

I have found some instructions to install a better nvidia graphics driver using the synaptic package manager which seemed to be working until I realized you needed Internet access which I didn't have as my network card wasn't working.

I have managed to get it working by downloading the driver source and running the following commands in terminal:

cd /home/user/LAN
cd src
sudo make
sudo make install
sudo modprobe atl1

However, now when I start synaptic it tells me I don't have administrative privileges and so can't perform changes! Grrr it's very annoying :frown: - this worked before when my network card didn't work and now it does I apparently don't have admin rights?

Any help will be greatly appreciated. I think I will be able to use Ubuntu a lot better when I have a descent screen resolution on there.

Many thanks,
 
      Brian

---

### Post by compmodder26 on 2007-04-06
How are you starting synaptic?  Are you getting to it from System->Administration, or are you typing it into the command line?  If it is the latter, you need to type "gksudo synaptic".

---

### Post by britonk on 2007-04-06
Thanks compmodder, before I read your post I think I found a way around the problem. I went into user and group admin and gave myself access to "root". When I start synaptic now it simply asks me for my password - sorted.

I still, however, don't have a decent graphics driver installed. The instructions I downloaded off the net to install "nVidia glx" via the Synaptic package manager havn't worked for some reason.

I therefore went to the nvidia web site and downloaded "NVIDIA-Linux-x86_64-1.0-9755-pkg2.run". nVidia says just type "sh NVIDIA-Linux-x86_64-1.0-9755-pkg2.run" to install the drivers. 

I tried this in terminal and it said I must be logged in as root. I tried to log in as root and ununtu says " the adminisstrator cann't log in from here". I therefore changed the boot sequence to start Linux without loading xwindows (by removing quiet splach and adding "single" to the command line and the nvidia program told me I am best running in level 3 mode rather that level 1 so i tried this and starting level 3 mode starts Ubuntu and I can't log in as root from there!!!!!

Is it just me or am I going round in circles? LOL

Does anyone know of an idiots guide to installing a decent nvidia driver? :sad:

---

### Post by zvacet on 2007-04-06
```
  sudo dpkg-reconfigure xserver-xorg
```
select **nvidia** If you have problem after that repete above command and replace** nvidia** with **nv** .After that find and install Envy script.I´m sure that you will find some link in this forum.

---

### Post by STREETURCHINE on 2007-04-06
link to envy script

            [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu4_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu4_all.deb)

---

### Post by britonk on 2007-04-07
That worked great I can choose from 1024X768, 800X600 or 640X480 now - thank you so much!

For some reason now that has been fixed my network driver has gone walkies. I tried to re-install it the same way I did before by running the following commands after CDing to the directory with the driver source files in it:

sudo make
sudo make install
sudo modprobe atl1

But now when I type "sudo make" I get an error message in terminal telling me the kernal source could not be found. Any ideas? This worked fine first time round and why has correcting my graphics problems got rid of my network card? :confused: 

Thanks so much guys the Ubuntu community are really helpful.

---

