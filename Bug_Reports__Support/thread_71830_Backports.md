---
title: "Backports"
date: 2005-10-04
forum: Bug Reports / Support
---

### Post by Spikey on 2005-10-04
Hi,

I have been reading alot of posts about the backports lately and how we have to remove the old backports and replace them with the new ones. I must admit that i am not really impressed with the new backports server that is up and running. There isnt nearly as many files available for download.

As an example: I tried to install PAN (Newsreader) by using  sudo apt-get install pan  and apt cant find the file in the new backports repository. 


Is there something i am missing? What other repositories are out there? Even if they arnt supported it doesnt matter to me. I just want to be able to find all the packages i need using apt-get.


Thanks
Spikey:D

---

### Post by aysiu on 2005-10-09
Even though I've read that it's not ideal to use non-Ubuntu repositories, I personally haven't had any issues using them. You can search them [here](http://www1.apt-get.org/search.php)

---

### Post by TristanMike on 2005-10-09
Well, in that particular case, it appears that "pan" is an offical projcect. Documentation can be found [here](http://packages.ubuntu.com/hoary/news/pan). So there's no reason you should have a problem installing it, it appears the problem with that may lie elsewhere.

Edit: of course that one is for Hoary, but fret not, it's in [Breezy](http://packages.ubuntu.com/breezy/news/pan)

---

### Post by jdong on 2005-10-09
Some backports were not legitimately packaged in the Mirrormax repositories (i.e. dependencies ignored or hacked against Hoary), and as a result eventually caused issues with other packages and upgrades.

Hoary has been a difficult release for the Backports team, because of all the bumps in the road. Fortunately, most of these issues have been ironed out for Breezy, and Dapper will certainly have a solid Backports+Extras collection.

---

