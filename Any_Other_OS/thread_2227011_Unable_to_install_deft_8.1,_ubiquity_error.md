---
title: "Unable to install deft 8.1, ubiquity error"
date: 2014-05-30
forum: Any Other OS
---

### Post by dubrewski on 2014-05-30
I currently have Ubuntu 14.04 and Kali installed on my laptop and trying to install deft forensics 8.1. As soon as the install begins I will get an error regarding usr/lib/ubiquity failing and it will switch to running in live mode. I have seen people have other ubiquity errors but none this early in the installation. I have checked the md5 value and it is correct. I have tried downloading it multiple times and have used several different USB thumb drives but I always recieve the same error. Can someone give me some pointers on what needs to be done to resolve this. Thanks.

---

### Post by superdalton on 2014-07-09
OK. I think i have a partner now. only that i am not sure how (if) you have figured out a solution to this issue.
i started the quest too and like you, i have Windows 8.1 installed working. i created all other partitions and want to have Ubuntu 14.04, Kali-Linux 1.0.7 and then deft 8.1.(in this order).
Ubuntu installed fine, but Kali-Linux didn't because there was no grub installed alongside. i have Google(d) round and couldn't fix the grub. i did all update, even along the installation and yet, the grub never came back. i later gave up, since my Ubuntu was already giving me the loader to Kali-Linux and it's working fine.
i think,in my case, the saving grace during Kali-Linux installation was that, there was a grub(Ubuntu) working and was used by my boot-repair(Live USB) to fix the Grub boot and loader for Kali-Linux.
Now to the order of the day, DEFT 8.1. i downloaded and before i could even prepare a Live USB it, i used all the USB creators that i have and downloaded more, none worked. Then i came to [Universal-USB-Installer-1.9.5.4]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/#more-3827") that helped produced the boot-able USB stick. as if that stress wasn't enough, installing became a problem as the installer didn't Install the DEFT8.1, instead it went to Live desktop and got me pissed off. after trying several times, i was able to check the errors and tried figuring what to do, but no luck and then no threads online talking about the installation of DEFT8.1. until i found this and i decided to share my experience.
The errors are shown below: 
[https://drive.google.com/file/d/0B81vq-ylJDe_UkNqT0dtQVFlVVU/edit?usp=sharing](https://drive.google.com/file/d/0B81vq-ylJDe_UkNqT0dtQVFlVVU/edit?usp=sharing)
[https://drive.google.com/file/d/0B81vq-ylJDe_TmVPUnRSYng5YVE/edit?usp=sharing](https://drive.google.com/file/d/0B81vq-ylJDe_TmVPUnRSYng5YVE/edit?usp=sharing)
[https://drive.google.com/file/d/0B81vq-ylJDe_TmVPUnRSYng5YVE/edit?usp=sharing](https://drive.google.com/file/d/0B81vq-ylJDe_TmVPUnRSYng5YVE/edit?usp=sharing)
[https://drive.google.com/file/d/0B81vq-ylJDe_Z2ZCeXJzbEw0WHc/edit?usp=sharing](https://drive.google.com/file/d/0B81vq-ylJDe_Z2ZCeXJzbEw0WHc/edit?usp=sharing)

looking forward to responses. i would keep the DEFT partition i have so that once a solution is proffered i can then install.
Thanks

---

