---
title: "Wireless connection problem: German letters not recognuzed"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-04-04
Hello,

here's my problem: I'm in Austria, my laptop has German keyboard. When I installed ubuntu (yesterday), I chose English as OS language and then changed keyboard language to German (Not the OS language). So now German keyboard works well and OS language is English. However, the OS has problem with recognition of german-specific letters ( ä, ö, ü, ß ) and puts "?"-symbol instead of them. The wireless network in my house is "Studentenheim_Rössl", it can find it, but when I write it in Network preferences, it can't be recognized. I tried with "Studentenheim_R?ssl", but it doesn't work either. Another wireless network, much weaker, is called "Linksys" and it works well, because it doesn't contain german letters.

Any ideas how can I overcome this language problem (the reason)? Please leave your suggestions. If you don't know the answer, then at least tell me how to change OS language to german without deleting partition with shared documents and "home"? (maybe update? how does one do that)

---

### Post by benfindlay on 2007-04-04
fire up a terminal and type ```
sudo dpkg-reconfigure xserver-xorg
```

You can reconfigure your keyboard settings in there, and set it to german(again). As far as I know you can maintain English as your language if you wish, or change it to a different one

As for changing the OS language, there should be an option in System>>Administration>>Language Support which you can change!

Hope this helps

---

### Post by drakazz on 2007-04-04
Try "sudo dpkg-reconfigure locales", just in case the xorg one does not work.

---

### Post by O-pos on 2007-04-05
I observed an important thing: the OS does indeed recognize german symbols, but not always: when I name files here in Linux, or when I import them, say, from USB of other computer to shared data partition in Linux, then the german ä ö ü letters in filemanes are recognized well. but If I import exactly the same files in my lap's windows (I have dual boot) again in shared data partition, they're not recognized and "?" in black quadrat is shown instead of them... the same is true If I named them in windows. maybe it's kinda compatibility problem and the same problem exists regarding WLAN aerials?

I tried ```
sudo dpkg-reconfigure xserver-xorg
``` and I got blue window asking me things about my video card. I have no idea what to answer. How can I reconfigure German settings? 

like I said, the keyboard language is already German, and when I write German letters, it's recognized, as is recognized German texts in .doc dociments or in webpages. 

however, on system level, it doesn't work: they are not recognized in filenames which I imported or downloaded from somewhere.


> **benfindlay said:**
> 
As for changing the OS language, there should be an option in System>>Administration>>Language Support which you can change!

Hope this helps
 It can be changed only to other English types, like US English, british, Australian, etc... No German.

> **drakazz said:**
> Try "sudo dpkg-reconfigure locales", just in case the xorg one does not work.

I tried this and I got following outout:

```

Generating locales...
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.
```
en_US  - american english is my OS' current language

---

### Post by eljalill on 2007-04-05
I am German myself, and long ago accepted, that some programs are just not made for that language... which is also why I have my system language as English... Although I don't have any proof, I always have the feeling that this messes things up less....

What do you need the network preferences for? Can't you do it another way? Maybe there is another program available with less problems?

But if you are set on doing this the way you started out with, you might also want to ask for help in the local forums, since this is language specific.
I know there is a German forum ([www.ubuntuusers.de](www.ubuntuusers.de)).

Viel Glück!

---

### Post by O-pos on 2007-04-05
Thanks for reply, actually I always use English for computers, but as my lap keybord is German (you know how it is with Y/Z letteres and the keys to the right), it should be German language for keyboard and English for everything else. but as I'm in Austria, I'm often encountering files and other items with names including german letters.

My network's name at home is "Studentenheim_Rössl". I'm new Ubuntu user and I don't know how to access this WLAN without entering network name in system>admin>networking>wireless connection>properties I don't know any other way. In windows it shows what networks are available and you simple click on it, but in Linux I can't/don't know how to do that.

---

