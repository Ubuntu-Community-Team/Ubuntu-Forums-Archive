---
title: "Debian - Checksums"
date: 2012-02-05
forum: Any Other OS
---

### Post by avnd on 2012-02-05
Hi!

I wanted to try out Debian GNU/Linux as a Live CD. So, I downloaded the .iso file for amd64 arch that came with xfce desktop through a torrent. I downloaded the torrent from Debian's website.

All I'm downloading is a single .iso image file under the name 'debian-live-6.0.3-amd64-xfce-desktop'. I wanted to check the md5sum of the downloaded image file. I'd been searching for the md5sums that I should compare the one I'm getting with. All I came up with was the following page.

[http://cdimage.debian.org/debian-cd/...64/web/MD5SUMS](http://cdimage.debian.org/debian-cd/...64/web/MD5SUMS)

The problem is that there is not one hash against the name of the file I'm downloading. Instead there are 4 for the xfce amd64 version, each for different files. 

I tried some searching and came with this page.

Verifying authenticity of Debian CDs

The above page was a little too complicated for my understanding. Can any one explain it better? It would be even better if someone could show me a page which gives the md5sums for the downloaded .iso file.

Thanks

---

### Post by haqking on 2012-02-05
> **avnd said:**
> Hi!

I wanted to try out Debian GNU/Linux as a Live CD. So, I downloaded the .iso file for amd64 arch that came with xfce desktop through a torrent. I downloaded the torrent from Debian's website.

All I'm downloading is a single .iso image file under the name 'debian-live-6.0.3-amd64-xfce-desktop'. I wanted to check the md5sum of the downloaded image file. I'd been searching for the md5sums that I should compare the one I'm getting with. All I came up with was the following page.

[http://cdimage.debian.org/debian-cd/...64/web/MD5SUMS](http://cdimage.debian.org/debian-cd/...64/web/MD5SUMS)

The problem is that there is not one hash against the name of the file I'm downloading. Instead there are 4 for the xfce amd64 version, each for different files. 

I tried some searching and came with this page.

Verifying authenticity of Debian CDs

The above page was a little too complicated for my understanding. Can any one explain it better? It would be even better if someone could show me a page which gives the md5sums for the downloaded .iso file.

Thanks


use md5sum for md5 hash (these are older CD's though

for newer ones use

sha1sums or sha512sums

read here [http://www.debian.org/CD/faq/#verify](http://www.debian.org/CD/faq/#verify)

the sums are in the same location you downloaded from [http://cdimage.debian.org/debian-cd/6.0.4/amd64/bt-cd/](http://cdimage.debian.org/debian-cd/6.0.4/amd64/bt-cd/)

---

### Post by avnd on 2012-02-05
Thanks for your rwply Haqking.

But I downloaded a live-CD image. I'm sorry I did not post the link to the md5sum page properly. The md5sums for the live-CD images are in the following page.

[http://cdimage.debian.org/debian-cd/6.0.3-live/amd64/web/MD5SUMS]("http://cdimage.debian.org/debian-cd/6.0.3-live/amd64/web/MD5SUMS")

The problem is that, this page has 4 md5sums for the live-cd image that I have downloaded. 

> 9f0ed37f3b2b290b9258389f5bc2be04  debian-live-6.0.3-amd64-xfce-desktop.initrd.img-2.6.32-5-amd64
ad525e8a7378f6d31795093b076a3967  debian-live-6.0.3-amd64-xfce-desktop.packages
2d76ec980f4b56e31fede1707abb0724  debian-live-6.0.3-amd64-xfce-desktop.squashfs
59164345a81d2a8aa12ae11f7f188419  debian-live-6.0.3-amd64-xfce-desktop.vmlinuz-2.6.32-5-amd64

Whereas I only have a single .iso image that I have downloaded. Which of the above do I compare my md5sum to?

---

### Post by haqking on 2012-02-05
> **avnd said:**
> Thanks for your rwply Haqking.

But I downloaded a live-CD image. I'm sorry I did not post the link to the md5sum page properly. The md5sums for the live-CD images are in the following page.

[http://cdimage.debian.org/debian-cd/6.0.3-live/amd64/web/MD5SUMS]("http://cdimage.debian.org/debian-cd/6.0.3-live/amd64/web/MD5SUMS")

The problem is that, this page has 4 md5sums for the live-cd image that I have downloaded. 



Whereas I only have a single .iso image that I have downloaded. Which of the above do I compare my md5sum to?

LOL well only one will compare ;-)

and it should be the one with the same file name as your download

besides 6.0.4 is the latest stable and the md5sums are in the link i posted previously along with the iso images

get the latest image here either CD or DVD and the sums are on same page [http://www.debian.org/CD/torrent-cd/](http://www.debian.org/CD/torrent-cd/)

for your architecture

[http://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/MD5SUMS](http://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/MD5SUMS)

and downloads [http://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/](http://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/)

---

### Post by avnd on 2012-02-08
Thank you, Haqking.

---

### Post by haqking on 2012-02-08
> **avnd said:**
> Thank you, Haqking.

you are welcome.

If you got it sorted then remember to use thread tools to mark the thread as solved.

Cheers

---

