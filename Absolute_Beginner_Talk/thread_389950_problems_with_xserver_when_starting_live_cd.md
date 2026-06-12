---
title: "problems with xserver when starting live cd"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by efthin on 2007-03-21
Hi, im booting from a live cd and im getting to the first menu where i can select installation options. Have tried to use the safe graphical start up too. I get this error message:

"fatal server error
no screens found
no devices found" 

so i tried to find an answer here in the forums before posting and tried this:

sudo dpkg -reconfigure xserver-xorg

and that only gave me the answer:

dpkg: conflicting actions -e (--control) and -r (--remove)

im having a ati radeon 850 XT

So how do i fix this so i can install ubuntu?

---

### Post by dracomordag on 2007-03-21
get rid of the space between dpkg and -reconfigure


sudo dpkg-reconfigure xserver-xorg

---

### Post by efthin on 2007-03-21
cheers, thougth i tried all combinations. Well now i configure everything. when thats done how do i restart the installation/start process?

---

### Post by lamalex on 2007-03-21
sudo /etc/init.d/gdm start
you may also want to try acpi=off in boot options. hit f6 when you can pick boot to live cd. this fixed my error.

---

### Post by dracomordag on 2007-03-21
i find a simple 

startx

 is much better than any of that.

---

### Post by efthin on 2007-03-22
thanks for all the answers but still not working :(


>  sudo dpkg-reconfigure xserver-xorg 

worked just fine, and i enter a setup and it detected my graphic card. I *think* i fill in all the right values in the setup. When i then use the startx command it gives me the same error as before. 

I have also tried the acpi=off thing in the boot options too, it made the computer crash even faster :(

i have tried to use the lspci command to see what values that i should use, but i cant get it to show me one page at the time (or scroll upwards when its done). 

 Im totally lost here, quite good with computers in general but im LOST when it comes to linux. All help are greatly appriciated!

So any suggestions what to do?

---

