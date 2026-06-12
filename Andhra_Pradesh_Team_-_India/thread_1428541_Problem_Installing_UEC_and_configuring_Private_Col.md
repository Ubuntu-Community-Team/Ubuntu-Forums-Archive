---
title: "Problem Installing UEC and configuring Private Colud"
date: 2010-03-12
forum: Andhra Pradesh Team - India
---

### Post by varunpandeyengg on 2010-03-12
Hey Guys,
I want to create a private cloud of my own. Its been a month now and i am not able to get it. Earlier I was trying to install Eucalyptus on Ubuntu 9.10 karmic. But its prerequisite ie xen  troubled me a lot while configuring. So i left that approach. Right now I have installed UEC from Ubuntu 9.10 server CD. I had few problems -

[LIST=1]
[*]Installation software failed to configure DHCP on Cluster as well as Node. Just to check I tried connecting my cluster and node with a cross lan. Configured ETH0 and pinging was done successfully. But /etc/networking/interfaces file is not present ony any of the machines. Am I doing any thing wrong?
[*]I am getting only terminal interface on my machines. Will there be any problem if I install the GUI seperately. What will be the packages I need to install?
[/LIST]
Can any one help me with this. Thanx in Advance... :)

---

### Post by geb1 on 2011-11-14
**UEC Installation Issues** 			 			 			 		   		 		 		ive tried many times to get uec 10 4 installed on diff tyes of computers 
I got cloud installed -the first time but  not sure if it included  cluster to walrus etc but I could not connect to it on port vi chrome  firefox etc 
i then installed node but despite best efforts could still not connect to cluster 
I then reinstalled cluster + all except node only to have software install step and grub install fail again and again 
Not sure if it was because I had node installed 
I tried on a laptop and was told that it could not take Uec hardware  error Sorry cant remember error but it had something to do with  virtualisation hardware -it is an older laptop.

I then installed it on pc that had node runningf  quad pc ( on another  hardrive ie i disconnect node hardrive  ) which  runs esxi 64bit no  problems but once again Cloud/*Cluster*/Storage/*Walrus* fails on software install and grub steps . It cant be hardware causing this 
I have now tried three computer and all fail on software install and grub step 

Therefore I am now convinced its a software problem. Possible reasons being 

1. Use of Lvm option 
2. cant be cos node installed cos I disconnect that and tried again and it still   failed 
3. perhaps its something to do with choosing all three options Cloud/*Cluster*/Storage/*Walrus*  i tried only cloud option but this also  failed so it cant be this 
4. perhaps its something to do with IP range I tried other closer ranges that I scanned as being available - no go 
5. perhaps the cloud ip must be outside range I tride this - still no go still software and grub step fail 
6. I checked bios but on the working  Esxi pc running 64 bit -nothing in  bios evens mentions  a virtualisation switch still no go 

I just cant recall if I had selected all three options on the original pc Cloud/*Cluster*/Storage/[I]Walrus on whcih i managed to get uec installed 
I do see that the three options are selected by default so I can safely  assunme that they where selected in the original install - the one that  gave me Http error on port connect 

[/I]*Hope this helps those also stuggling with same problem *
[I]Basicacly Im stuck 

any ideas ?[/I]

---

