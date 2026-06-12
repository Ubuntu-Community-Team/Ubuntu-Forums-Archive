---
title: "Fiesty and VMWare Server"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by harperd on 2007-05-10
After installing Fiesty, VMWare Server refused to run - the bouncing icon just bounces for a while and then disappears. I've checked the forums and seen a fix but it doesn't work, at least for me. 

Has anyone got a fix? Also, I've installed Virtual Box and wondered if I can use the virtual machine I created previously with VMWare with Virtual Box. I don't want to go through the hassle of installing and setting up XP again.

Thanks - Dave in Spain

---

### Post by Bachstelze on 2007-05-10
The kernel modules VMware uses are not compatible with FEisty's 2.6.20 kernel. However, there's a patch available for it. Do you stil have the vmware installation tarball ?

---

### Post by harperd on 2007-05-12
Yep! I'm a little concerned that VMWare will keep breaking as Ubuntu develops. Would a different option be better? Thanks.

---

### Post by in_flu_ence on 2007-05-12
I can't say that it will/will not break for certain. However, I think vmware is still among the top option for virtualisation in term of user-friendliness (at the moment) and features. Virtual Box doesn't give me the choice in 64bit yet.

Most likely problem with vmware that I have encountered is the bridged network. However, the vmware-any-any patch seems to update pretty frequently. There were also some problem with using madwifi (ath0) as your network interface but i think it is an easy fix.

To me, I think vmware will face similar problem when you try to upgrade from XP to vista (but I am not sure). However, you have the option to upgrade your system at any time for Ubuntu. You are not obliged to upgrade to the next verion every 6 month. You can always wait till things are stable in the next version before upgrading. Of course the LTS version offers you the stability (if you need it).

So i think vmware will be my definite choice but rather I will regulate my upgrade timeframe to minimise 'breakage' along the path.

---

### Post by Bachstelze on 2007-05-12
The VMware "breakage" has nothing to do with Ubuntu. The VMware modules just won't compile on a 2.6.19+ kernel, in any distro, not just Ubuntu.

---

### Post by veloce on 2007-05-13
> **HymnToLife said:**
> The VMware "breakage" has nothing to do with Ubuntu. The VMware modules just won't compile on a 2.6.19+ kernel, in any distro, not just Ubuntu.

The ubuntu feisty repositories now include compiled modules.

---

### Post by harperd on 2007-05-15
I've had no success in getting VMWare to work despite using the patch. I'm about to give up! Thanks for the message  "The ubuntu feisty repositories now include compiled modules" - what do I have to do? Thanks.

---

### Post by Zafrusteria on 2007-05-15
Did you see this post from Veloce,? It sorts out the VMware installation problem by adding the repositories for vmware.  Just install as usual using the Synaptic package manager.

> [http://ubuntuforums.org/showthread.php?t=442924&highlight=vmware+server](http://ubuntuforums.org/showthread.php?t=442924&highlight=vmware+server)


---

### Post by desicratn on 2007-05-15
I just did this last night...

Add this to the repositories[ admin>Software sources ( 3rd party software sources)]: 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

then re load synaptic and it will be under VMWare Server it will install everything automatically. just make sure you clean up any previous installs of VMWare Server or player.

---

### Post by harperd on 2007-05-16
Thanks, I'll try it later. By cleanup do we mean uninstall?

---

### Post by zvacet on 2007-05-16
Yes,uninstall.Old installation will prevent you to install new one.Install it from synaptic.It is 1.0.2 version andif you want 1.0.3 go here 

[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto?]("http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto?")

---

### Post by veloce on 2007-05-16
> **zvacet said:**
> Yes,uninstall.Old installation will prevent you to install new one.Install it from synaptic.It is 1.0.2 version andif you want 1.0.3 go here 

[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto?]("http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto?")

As of this morning, the repo now has VMware Server 1.03

Upgrade successfully completed!

---

### Post by bodhi.zazen on 2007-05-16
> **harperd said:**
> Has anyone got a fix? Also, I've installed Virtual Box and wondered if I can use the virtual machine I created previously with VMWare with Virtual Box. I don't want to go through the hassle of installing and setting up XP again.

Thanks - Dave in Spain

I hope you fix you issue with VMWare server.

But, to answer your question regarding VirtualBox, yes you can convert your WM machine to virtual box :

[http://doc.gwos.org/index.php/VirtualBox#Convert_a_VMWare_appliance](http://doc.gwos.org/index.php/VirtualBox#Convert_a_VMWare_appliance)

---

### Post by harperd on 2007-05-22
Thanks for the help guys. I finally got it working although it didn't appear on the KDE menu so I'm just typing vmware from the command line. I had some problems configuration the network adaptor but managed to get it working eventually.

---

### Post by veloce on 2007-05-22
> **harperd said:**
> Thanks for the help guys. I finally got it working although it didn't appear on the KDE menu so I'm just typing vmware from the command line. I had some problems configuration the network adaptor but managed to get it working eventually.

Make sure you write down what you did to get the networking working - when you update, all the network settings go back to their defaults!

I added an icon on the tool bar to run vmware - I searched around and found the icon so it looks right as well.  (Then when I updated it turned up in the menu again - go figure).

---

