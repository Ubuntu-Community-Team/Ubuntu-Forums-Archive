---
title: "md5sum"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by jjefferies on 2007-08-09
Where does one find the md5sum for Ubuntu cd iso images? I downloaded the UbuntuMedia CD from
 [http://linux.softpedia.com/progDownload/Ubuntu-Multimedia-Center-Download-20678.html](http://linux.softpedia.com/progDownload/Ubuntu-Multimedia-Center-Download-20678.html)

K3B indicates that "This image has an invalid file size.If it has been downloaded make sure the download is complete." I run md5sum on the iso image and the value returned is: 
26b988eaf0e6b37b5420d01725b2c139  Ubuntu Multimedia Center.iso
which is also the value calculated by K3B.

So where can I find the md5sum values for the iso so as to be able to determine if the download was complete?

thanks

---

### Post by SeanTater on 2007-08-09
I imagine you will find it more worthwhile to download ubuntu from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

But if you burn and then boot from the cd it has an option to check itself, so md5sum is unnecessary..

---

### Post by forestpixie on 2007-08-09
there's a list here
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by asmoore82 on 2007-08-09
^^^ ungh that page almost makes me sick with all the inline javascript pop-ads
AND not giving you an md5 to check against ...
this also jumped out at me ...

```
Last Updated:  	December 5th, 2006 10:33
```

maybe you should give Ubuntu Studio a try... it's more official and keeps up with the release schedule.
their site ubuntustudio.org seems to be busy or down right now, but you can still get the iso by
googling for 'ubuntu studio mirror'

---

### Post by forestpixie on 2007-08-09
> **SeanTater said:**
> I imagine you will find it more worthwhile to download ubuntu from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

+1
that;'ll be better for you - or a torrent

But I'd check the hash before you burn - so that at least you'll know you're starting out ok. 

I know K3b will check before it burns - as do you. That hash number doesn't appear to be on the list though.

---

### Post by forestpixie on 2007-08-09
> **asmoore82 said:**
> 
```
Last Updated:  	December 5th, 2006 10:33
```

maybe you should give Ubuntu Studio a try... it's more official and keeps up with the release schedule.
their site ubuntustudio.org seems to be busy or down right now, but you can still get the iso by
googling for 'ubuntu studio mirror'

I don't know whether I'd say Studio was more official?

And there's a last edited date 21st 04 2007 

Any way I'd be inclined to say you'll need to download again one way or the other

---

### Post by por100pre1 on 2007-08-09
If you are using windows use [winmd5sum]("http://www.nullriver.com/index/products/winmd5sum") to check iso's md5. It's easy.

---

### Post by por100pre1 on 2007-08-09
> **forestpixie said:**
> I don't know whether I'd say Studio was more official?

And there's a last edited date 21st 04 2007 

Any way I'd be inclined to say you'll need to download again one way or the other

I don't know how official is Ubuntu Studio neither,  but I know that it uses mostly Ubuntu repos and that it can be installed (and uninstalled) easily on a existing Feisty installation. That makes Ubuntu Studio a better bet. 
:guitar:

---

### Post by forestpixie on 2007-08-09
Yea sorry all  - didn't see the media in the Ubuntu :oops: - so the hashes would have been quite useless as well  - wondered why I  didn't get asmoore82  popups and date

---

### Post by asmoore82 on 2007-08-09
> **forestpixie said:**
> Yea sorry all  - didn't see the media in the Ubuntu :oops: - so the hashes would have been quite useless as well  - wondered why I  didn't get asmoore82  popups and date

yea, :p you can't get any further from official than softpedia :lol: ... well, cnet :shudder:

---

### Post by forestpixie on 2007-08-09
I saw the softpedia - then Ubuntu and closed my eyes :)

---

### Post by por100pre1 on 2007-08-09
> **asmoore82 said:**
> yea, :p you can't get any further from official than softpedia :lol: ... well, cnet :shudder:

That was good!
:lolflag:

---

### Post by jjefferies on 2007-08-09
> **SeanTater said:**
> I imagine you will find it more worthwhile to download ubuntu from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

But if you burn and then boot from the cd it has an option to check itself, so md5sum is unnecessary..
Unfortunately I was unable to locate a multimedia version of ubuntu at ubuntu.com which was the first place I looked.  I do have the 7.04 release on a CD passed out at Linux world yesterday. But I was advised that the multimedia version would be more useful for what I am interested in. And the only site that I could find with the iso to be downloaded is softpedia.

 If the disk checks itself when booting I suppose that I will have to trust that though I would prefer to check the hash after downloading. That is unless someone can correct me and point me to a nice site with the latest release with multi-media.

thanks
jjefferies

---

