---
title: "Complete noob: Questions  mainly on installing"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by invader980 on 2006-03-11
:confused: This is my first attempt at linux ever so ur gonna have to bare with me ..... as truthlly i have no idea what im talkin about lol... but if ur willing to help me find out :

1) I am having trouble understanding how to install anything .. ive read up on rpm, and archives ... but as far as going threw a complete installation i have yet to accomplish.. 
- Running the rpm command i retrive this error " bash: rpm: command not found"
 which i can only chulk up to ... im missing somthing  lol

2) ive downloaded tar archives that where c sources and got as far as decompressing,,, trying to run configure for most of these packaged  gives me the following error:

*/
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
/*

- so i googled for a while found the homepage for gcc... when i realized i dont even know how to download the dirtributions from the ftp sites.... 

-- can anyone help me with some basics , and/or help me solve these problems this is like learning how to crawl all over again lol..
-- im sure  uve gotten them befor but i cant seem to break down the tuts  having 0 knowlege .... 

thanx prior

---

### Post by aysiu on 2006-03-11
Ubuntu doesn't use RPMs natively, and you don't need to install from source for most applications. Read more here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Q4U on 2006-03-11
1. Ubuntu is a Debian derivative, i.e. it uses .deb packages, not .rpm (that is why you get the "rpm not found" error. If you want to install some binary packages from the official repositories, use the utility called apt (from the command line) or synaptic (graphical, very newbie friendly). If you want something from the unofficial repositories, you need to manually edit your /etc/apt/sources.list file to include the repositories.

2. If you want to install from source, you need to install the "build essentials" packages, which are not included by default in the installation.

Hope this helps. Q

---

### Post by taurus on 2006-03-11
You can convert .rpm to .deb before you install it on your system...
```

sudo apt-get install alien
sudo alien filename.rpm
sudo dpkg -i filename.deb

```

---

### Post by aysiu on 2006-03-11
You can also save yourself a step and ```
sudo apt-get install alien
sudo alien -i filename.rpm
```

---

