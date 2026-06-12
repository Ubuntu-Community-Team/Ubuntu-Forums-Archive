---
title: "No sound in online videos"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by danieltowsey on 2006-12-22
Hi  I am very new to linux..after a rough start I have been able to get things working good. thanks to the help from members of this forum..But now I have another problem..When ever I watch on line videos like Utube. I have no sound. This is the same for all video formats but if I listen to a mp3 online, I do have sound..any ideas? Thanks for your help.

---

### Post by user007usa on 2006-12-22
> **danieltowsey said:**
> Hi  I am very new to linux..after a rough start I have been able to get things working good. thanks to the help from members of this forum..But now I have another problem..When ever I watch on line videos like Utube. I have no sound. This is the same for all video formats but if I listen to a mp3 online, I do have sound..any ideas? Thanks for your help.

Look into automatix2 or easyubununtu to install particularly the flash plugins so that they will work with your browsers.

Also I have noticed that there is a problem where sometimes if one application is open (say rhythmbox and is using the sound card) other applications may be locked out.  Try to close any application which is using the sound card.  I am unaware of any other workaround for this unfortunately.

Which browser are you using btw?

---

### Post by danieltowsey on 2006-12-22
> **user007usa said:**
> Look into automatix2 or easyubununtu to install particularly the flash plugins so that they will work with your browsers.

Also I have noticed that there is a problem where sometimes if one application is open (say rhythmbox and is using the sound card) other applications may be locked out.  Try to close any application which is using the sound card.  I am unaware of any other workaround for this unfortunately.

Which browser are you using btw?
I am using firefox..but what is 'automatix2 or easyubuntu'?

---

### Post by user007usa on 2006-12-22
> **danieltowsey said:**
> I am using firefox..but what is 'automatix2 or easyubuntu'?

They are utilities meant for new users to make common tasks easier -- like installing the codecs needed to watch certain videos or getting the flash player set up in firefox.

There is automatix2: [http://www.getautomatix.com/](http://www.getautomatix.com/)

and then there is Easyubuntu: [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

Officially, EasyUbuntu is more supported and "official".  But I used automatix2 on my 6.10 (edgy) install and it worked great.  Of the two EasyUbuntu is probably a little bit easier to set up.  Have a look.  You are probably better off trying EasyUbuntu.

---

### Post by danieltowsey on 2006-12-22
> **user007usa said:**
> They are utilities meant for new users to make common tasks easier -- like installing the codecs needed to watch certain videos or getting the flash player set up in firefox.

There is automatix2: [http://www.getautomatix.com/](http://www.getautomatix.com/)

and then there is Easyubuntu: [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

Officially, EasyUbuntu is more supported and "official".  But I used automatix2 on my 6.10 (edgy) install and it worked great.  Of the two EasyUbuntu is probably a little bit easier to set up.  Have a look.  You are probably better off trying EasyUbuntu.
Thanks

---

### Post by Dr. C on 2006-12-22
If another applicaton is locking the sound card then I have found the following works in a terminal

```

sudo killall artsd

sudo killall esd
```

---

### Post by iPirates on 2006-12-24
So, automatix2 and EasyUbuntu are essentially the same thing?

Is one "better" than the other? 
 If not, i'll probably just install EasyUbuntu (being easier and all)

---

### Post by Goth Mneph on 2006-12-28
thanx user007usa, i've i almost gave up on linux as a whole because i couldn't get sound when i was online.  that easyubuntu program did the trick.

happy surfing to all.

---

