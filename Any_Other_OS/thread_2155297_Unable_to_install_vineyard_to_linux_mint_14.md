---
title: "Unable to install vineyard to linux mint 14"
date: 2013-06-17
forum: Any Other OS
---

### Post by ldtexan on 2013-06-17
Please help.  I a newbie to linux and i really need all the help i can get.  

when i  tried to install vineyard, i get the following error message.  

W: Failed to fetch [http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
cowboy@cowboy-System-Product-Name ~ $ sudo apt-get install vineyard
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vineyard : Depends: python-support (>= 0.90.0) but it is not installable
E: Unable to correct problems, you have held broken packages.



any and all help  is grealy appreciated. 
thank you.
ld

---

### Post by grahammechanical on 2013-06-20
May I suggest that you are using the wrong PPAs? Did you get your information from here?

[http://vineyardproject.org/download/](http://vineyardproject.org/download/)

Oh, do not forget that wine should be installed first.

Regards.

---

### Post by ldtexan on 2013-06-22
Sorry  for the delay.
Wine is and was installed first.  And yes I did use  the site that you suggested.  Todate,  I  have searched the internet to noavil and have  went to the book store looking  for any help with no luck. So now I am lost and not sure which direction to go.  I was hoping to be able to rid myself of Windows, but it looks like I will have to keep it  around for now.  
I do thank you for your help.  
LD

---

