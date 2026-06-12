---
title: "[SOLVED] How to install a Linux driver for a wifi adaptor?"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-08-21
[img]http://www.tcpshop.com/shop/data/61/3com1_2.jpg[/img]

I do have a 3com 54g USB adaptor which I had great plans for using with Feisty Fawn, but am at a loss on how to install this driver.


The adaptor is the 3COM  3crusb10075

All drivers are available on this page

```


http://www.3com.com/products/en_US/result.jsp?selected=all&sort=effdt&sku=3CRUSB10075&order=desc


```

There is a Linux driver for the adaptor listed on the above

 linux_3CRUSB10075_drv_1_2_0_0.tar.gz    	 	  

```


http://webprd1.3com.com/swd/jsp/user/index.jsp?id=WUSBL1


```

There is a text file with instructions, but am not that savvy on how to go about doing this in the 1st place.


Some help would be appreciated :)

---

### Post by ddrichardson on 2007-08-21
It looks like you need to decompress, make and make install:
```
tar xvfz linux_3CRUSB10075_drv_1_2_0_0.tar.gz
cd linux_3CRUSB10075_drv_1_2_0_0
make
sudo make install
```

---

### Post by overdrank on 2007-08-21
> **chrome307 said:**
> [img]http://www.tcpshop.com/shop/data/61/3com1_2.jpg[/img]

I do have a 3com 54g USB adaptor which I had great plans for using with Feisty Fawn, but am at a loss on how to install this driver.


The adaptor is the 3COM  3crusb10075

All drivers are available on this page

```


http://www.3com.com/products/en_US/result.jsp?selected=all&sort=effdt&sku=3CRUSB10075&order=desc


```

There is a Linux driver for the adaptor listed on the above

 linux_3CRUSB10075_drv_1_2_0_0.tar.gz    	 	  

```


http://webprd1.3com.com/swd/jsp/user/index.jsp?id=WUSBL1


```

There is a text file with instructions, but am not that savvy on how to go about doing this in the 1st place.


Some help would be appreciated :)

HI maybe this thread will help
[http://ubuntuforums.org/showthread.php?t=328314&highlight=3COM+3crusb10075](http://ubuntuforums.org/showthread.php?t=328314&highlight=3COM+3crusb10075)

---

### Post by teaker1s on 2007-08-26
you need to look at this before you try compiling

[https://help.ubuntu.com/community/teaker1s?highlight=%28teaker1s%29#head-7122eba654269ea93933b2ca057919c42ec2cd6d]("https://help.ubuntu.com/community/teaker1s?highlight=%28teaker1s%29#head-7122eba654269ea93933b2ca057919c42ec2cd6d")

---

### Post by chrome307 on 2007-08-26
I got this working with the advice posted here by a helpful member :)

[http://ubuntuforums.org/showthread.php?t=534617](http://ubuntuforums.org/showthread.php?t=534617)

---

