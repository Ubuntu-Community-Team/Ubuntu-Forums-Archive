---
title: "Problem with updating..."
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by tyboon on 2007-04-28
i run this comand  on the terminal.... sudo apt-get update ....
and this is what i got....

Fetched 28.0kB in 3s (7278B/s)
Reading package lists... Done
W: GPG error: [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5B638EFECEAE2DE7
W: GPG error: [http://www.telemail.fi](http://www.telemail.fi) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFFF5E937215FF
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 576856718434D43A
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
hvasss@hvasss-desktop:~$ 
i always get like a GPG error...something about key..
can anybody help...?I also cant update through the update manager..
Thanx

---

### Post by mikeyphi on 2007-04-28
Try the procedure at this official guide:  [http://www.ubuntulinux.org/getubuntu/upgrading](http://www.ubuntulinux.org/getubuntu/upgrading)

---

### Post by tyboon on 2007-04-28
i run my system with feisty..i did  the upgrade procedure and everything was ok..but i have this problem with the updates...i Dont get updates

---

### Post by mikeyphi on 2007-04-28
Hi !! - Sorry - obviously didn't understand the problem.....
Have you got all the Boxes ticked under Software Sources?

---

### Post by tyboon on 2007-04-28
No.... :lolflag: How would i do that?Could you help me..?

---

### Post by tyboon on 2007-04-28
well all my boxes are ticked...it should be workin and updating.. but this is what i get..

W: GPG error: [http://www.telemail.fi](http://www.telemail.fi) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFFF5E937215FF
W: GPG error: [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5B638EFECEAE2DE7
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 576856718434D43A
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

So...anybody knows how i would get this keys...?
I would be most thankfull...

---

### Post by mikeyphi on 2007-04-28
Try after changing the 'Download from' to the main server (or some other server) under Software Sources

---

### Post by DougieFresh4U on 2007-04-28
For medibuntu, copy & paste in terminal:
**wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -**

---

### Post by DougieFresh4U on 2007-04-28
Try this:
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]

---

### Post by tyboon on 2007-04-28
this is what i got..

hvasss@hvasss-desktop:~$ gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg: directory `/home/hvasss/.gnupg' created
gpg: can't open `/gnupg/options.skel': No such file or directory
gpg: keyring `/home/hvasss/.gnupg/secring.gpg' created
gpg: keyring `/home/hvasss/.gnupg/pubring.gpg' created
gpg: "KEY" not a key ID: skipping
hvasss@hvasss-desktop:~$ sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
Password:
gpg: "KEY" not a key ID: skipping
hvasss@hvasss-desktop:~$ sudo  gpg --export --armor KEY | sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
hvasss@hvasss-desktop:~$ 

i Dont know...i followed this tutorial and i idi everything the way i should..i even tried the troubleshooting..have a look and tell me if i did something wrong... + i upgrated the edgy to feisty but i followed the how to for feisty...may thats wrong???
what else...if you have any idea just tell me...
Thanx for your time..

---

### Post by DougieFresh4U on 2007-04-28
My mistake. In the "Search" , next to "Quick Links" type GPG keys or public keys and look through all the post that come up, as your problem is not "unique' and has been discussed before and there are many anbswers there. sorry I don't know about the "tuxfamily" key
Good luck. I shall check back later:)

---

### Post by tyboon on 2007-04-28
I would really appreciate if someone could tell me how my source list would look like..still i dont get any updates..still didnt figure it out..this is how it looks..i think i messed up with the repositories...how can i fix that..i am still a begginer..
this is what i get when i give sudo apt-get update ...

hvasss@hvasss-desktop:~$ sudo apt-get update
Get:1 [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) feisty Release.gpg [189B]
Ign [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) feisty/main Translation-en_US                   
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US                    
Hit [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) feisty Release                                  
Get:3 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/exaile Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US              
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Get:5 [http://www.telemail.fi](http://www.telemail.fi) feisty Release.gpg [189B]                         
Err [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) feisty Release                                  
  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US           
Get:7 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [191B]                
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US     
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_US           
Get:9 [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) feisty Release [6716B]                        
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_US              
Get:10 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [11.9kB]                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_US       
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Ign [http://www.telemail.fi](http://www.telemail.fi) feisty/fonts Translation-en_US                      
Ign [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) feisty Release                                  
Get:12 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                          
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release                             
Hit [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) feisty/main Packages                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Hit [http://www.telemail.fi](http://www.telemail.fi) feisty Release                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages           
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages              
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages                       
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/exaile Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages  
Err [http://www.telemail.fi](http://www.telemail.fi) feisty Release                          
  
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Sources          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Sources      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US   
Get:13 [http://www.telemail.fi](http://www.telemail.fi) feisty Release [1221B]
Ign [http://www.telemail.fi](http://www.telemail.fi) feisty Release       
Ign [http://www.telemail.fi](http://www.telemail.fi) feisty/fonts Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release
Ign [http://www.telemail.fi](http://www.telemail.fi) feisty/fonts Sources                        
Hit [http://www.telemail.fi](http://www.telemail.fi) feisty/fonts Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources
Hit [http://www.telemail.fi](http://www.telemail.fi) feisty/fonts Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Fetched 20.6kB in 5s (3739B/s)
Reading package lists... Done
W: GPG error: [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5B638EFECEAE2DE7
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 576856718434D43A
W: GPG error: [http://www.telemail.fi](http://www.telemail.fi) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFFF5E937215FF
W: You may want to run apt-get update to correct these problems
hvasss@hvasss-desktop:~$ 

What about those 3 GPG errors.. anybody knows anything...?:confused:

---

### Post by minhamra on 2007-07-05
Although the post was from March, I just had the same problem and traced it to an Avant AWN dock. You can get the key here

wget [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg) -O- | sudo apt-key add -

Hope this helps.

---

### Post by funnypanks on 2007-08-26
> **minhamra said:**
> Although the post was from March, I just had the same problem and traced it to an Avant AWN dock. You can get the key here

wget [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg) -O- | sudo apt-key add -

Hope this helps.

you just saved me a lot of problems.

---

