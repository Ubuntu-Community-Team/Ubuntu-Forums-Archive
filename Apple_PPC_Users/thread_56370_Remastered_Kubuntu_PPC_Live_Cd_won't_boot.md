---
title: "Remastered Kubuntu PPC Live Cd won't boot"
date: 2005-08-12
forum: Apple PPC Users
---

### Post by YoG%*@ on 2005-08-12
hi, 

i'm currently working on a custom kubuntu hoary live cd for an ibook g3 and followed the instructions of the [LiveCdCustomizationHowTo](https://wiki.ubuntu.com/LiveCDCustomizationHowTo?highlight=%28cd%29%7C%28live%29%7C%28customization%29)
everything seemed to work fine, made the iso, burnt it, put in my cd drive, held down the c key... but the cd didn't boot. 
i stuck to the instructions in the howto, is there anything else i should have paid attention to? 

any help would be appreciated!

---

### Post by YoG%*@ on 2005-08-16
hm... i'll try to be more specific, maybe that helps

the notebook i'm working with is an ibook g3, 

the remastered iso was generated using this commando:
$ sudo mkisofs -r -V "Custom Ubuntu Live CD" \
            --netatalk -hfs -probe -map hfs.map \
            -part -no-desktop \
            -hfs-bless extracted_cd/install \
            -hfs-volid Ubuntu/PowerPC_hoary \
            -o custom-hoary-live-powerpc.iso extracted_cd

and then i burned the iso with k3b at low speed to insure it is no cd reading / whatever error.

i even tried the whole remastering process without changing a thing and then putting it back together, which still did not boot. 

when holding c during boot i am prompted three times to either press c for booting from cdrom or any other key to boot linux and after that it hangs and i have to reboot.

i'd be thankful for any help or solutions or hints where to start looking for mistakes! is the way the .iso file is created totally correct? 

thanks in advance, mux

---

