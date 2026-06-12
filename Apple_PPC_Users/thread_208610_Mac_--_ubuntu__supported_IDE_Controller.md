---
title: "Mac -- ubuntu  supported IDE Controller"
date: 2006-07-03
forum: Apple PPC Users
---

### Post by Shindigy on 2006-07-03
I am about to obtain a Mac G3 B&W, and my use for it will be running ubuntu as the OS. Should I pick out hardware compatible with a Mac or with Linux? I am thinking Linux because hardware is hardware and the OS needs to know how to work with it, but does the Mac BIOS (or equivalent) need to recognize it? I can not find any controllers that are listed/tested (or just flat out work) on both OSs.

Here is a link to a controller I am thinking about getting.
[http://www.newegg.com/Product/Product.asp?Item=N82E16815124001](http://www.newegg.com/Product/Product.asp?Item=N82E16815124001)

Mitch

---

### Post by benford on 2007-02-06
Hello everyone, this is my first post to the Ubuntu forums. 

I'm facing a similar problem. I have set up a a grey G4 tower (likely sawtooth or yikes! variant)  which runs off Ubuntu 6.06 server edition. It is used primarily as a backup system, so I have a usb 2.0 drive  (300 GB) as main storage space, with the smaller (around 10 GB) IDE drive holding the OS. The external drive is IDE, but it is over the 137ish GB limit that the built in IDE controller can handle. The external enclosure is beginning to fail, so I am considering buying a PCI based IDE card so that the machine can use the 300 GB disk internally. Does anyone have a confirmed IDE controller card which would work with this setup? I have some newegg links that I am considering here:

[http://www.newegg.com/product/product.asp?item=N82E16816102007](http://www.newegg.com/product/product.asp?item=N82E16816102007)
This one worked with SuSE according to review comments

[http://www.newegg.com/product/product.asp?item=N82E16816115008](http://www.newegg.com/product/product.asp?item=N82E16816115008)
This supposedly works with SuSE, Red Hat, Caldera and Turbo Linux.

[http://www.newegg.com/product/product.asp?item=N82E16816123006](http://www.newegg.com/product/product.asp?item=N82E16816123006)
The above has alleged success with Fedora Core 5. Would the same work for Ubuntu PPC?

All of them have Linux support according to the specifications tab. Will any of them work with Ubuntu PPC  (kernel 2.6.15-27-powerpc) with a minimum of hassle and configuration? If not these, are there particular models which I should look out for?

(edit)
I just found this card, designed for MacOS 8.5/9/X. Would it be supported by Ubuntu PPC?
[http://www.newegg.com/Product/Product.asp?Item=N82E16816123110](http://www.newegg.com/Product/Product.asp?Item=N82E16816123110)

---

### Post by grazie on 2007-02-06
Shindigy,

I have a B&W Powermac which is well known for IDE controller issues and I had a lot problems installing Gentoo on it about a year ago. However, I then tried Ubuntu and it was no problem whatsoever. Unless you already have problems with this machine as it is, I wouldn't bother getting the IDE controller.

Also the BIOS equivalent is OpenFirmware.

---

