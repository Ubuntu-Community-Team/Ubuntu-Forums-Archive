---
title: "Adobe flash player install [Resolved]"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Jesiah76 on 2007-01-03
Can anyone tell me why I get this message when I try to install flash player:

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.

It says complete but when I try to use something with flash player it still does not work. 
I dont know where the components directory is in the Mozilla browser, can anyone point me in the right direction please?

---

### Post by kngz on 2007-01-03
IAm new here but have been running all  differnet types of linux op systems and betwenn  unbntu,D.S.L=damn small linux I cant  pick which one I like more. But flash player is not that  good on the Internet it sucks and ther for it shouldn't be that hard to install  if you get that message copy and paste it in a termail window with h at the end and it should help you get through it .

---

### Post by Jesiah76 on 2007-01-03
Thanks I appreciate that

---

### Post by Jesiah76 on 2007-01-03
I just tried to get back in that web site and now it says that it requires adobe flash player 8 or higher and the version I downloaded was 7. 
Is there a newer version than 7?? or at least in developement? or anyother alternative to adobe flash?

---

### Post by Efwis on 2007-01-03
> **Jesiah76 said:**
> I just tried to get back in that web site and now it says that it requires adobe flash player 8 or higher and the version I downloaded was 7. 
Is there a newer version than 7?? or at least in developement? or anyother alternative to adobe flash?

get automatix2, it will install Flash 9 for you, and it does work. and you don't have to do any command line if you don't want to.

open synaptic and search for automatix. install and have a ball.

---

### Post by Jesiah76 on 2007-01-04
thanks once again

---

### Post by Jesiah76 on 2007-01-04
one more thing, how do I do that?

---

### Post by riven0 on 2007-01-04
To get to Synpatic Package Manager: System >> Administration >> Synaptic Package Manager.

Now, go to Settings >> Repositories and make sure all the sections under Internet are checked off. Click Ok and Reload. Then do your search.

---

### Post by obsidion on 2007-01-04
> **Jesiah76 said:**
> I just tried to get back in that web site and now it says that it requires adobe flash player 8 or higher and the version I downloaded was 7. 
Is there a newer version than 7?? or at least in developement? or anyother alternative to adobe flash?

 Ok what is happening is that it is trying to install globally and as a normal user you don't have permission to do that.

The easiest way is to install flash 9 from adobe
[http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

 Downlaod that and then you need to use a terminal, a can be a bit scary but as long as you are careful most mistakes are recoverable :)
 I suggest that you install yakuake, go to synaptic and do a search and let it install the dependencies, it is a kde app so if you are a ubuntu/gnome use it will need some libraires. Once installed and run it only requires you to push F12 to open it and is very configurable.

  Anyway either do that or open a terminal program if you want, you will be in your home directory
type ls to list what is there and see what your download is called, if you haven't modifired the directory in firefox you need to cd Desktop to find it. Note the capital D. I'm not sure how much you know about using linux so forgive me if I am being too simple :)

 Once you find the file, it will probably be FP9_plugin_beta_112006.tar.gz but you don't need to type all that in a terminal tab is your friend, so type tar zvxf FP9 and hit tab to autocomplete and then enter it will create another directory called flash-player-plugin-9.0.21.78  cd to that directory, again use tab.

once you are there ls to get the name of the file probably libflashplayer.so

now
sudo cp libflashplayer.so /usr/lib/firefox/plugins/  enter

Now restart firefox and check for installed plugins type aboutplugins but put a : between the t and p I did it that way because it puts a smilie otherwise, in the address bar of firefox. Again applogies if I seem to be telling you to suck eggs.

---

### Post by aysiu on 2007-01-04
I wrote up a quick little HowTo on Flash 9 beta. You may find it useful.
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by obsidion on 2007-01-04
> **aysiu said:**
> I wrote up a quick little HowTo on Flash 9 beta. You may find it useful.
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)


   Bookmarked, it is better written than my how to :)

---

### Post by Jesiah76 on 2007-01-04
thanks again everyone.

---

### Post by Jesiah76 on 2007-01-04
well I got it working with all of your help. thank all of you once again.

---

### Post by Cariboo1938 on 2007-01-07
> **aysiu said:**
> I wrote up a quick little HowTo on Flash 9 beta. You may find it useful.
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)Is Flash 9 Beta stable? Does it work for Ubuntu6.10-amd64

---

### Post by aysiu on 2007-01-07
> **Cariboo1938 said:**
> Is Flash 9 Beta stable? Does it work for Ubuntu6.10-amd64
Yes, it's pretty stable. As for AMD64, you can try [this HowTo](http://www.ubuntuforums.org/showthread.php?t=290785).

---

### Post by Cariboo1938 on 2007-01-08
> **aysiu said:**
> Yes, it's pretty stable. As for AMD64, you can try [this HowTo](http://www.ubuntuforums.org/showthread.php?t=290785).Thanks aysiu, for the hint. I checked and didn't dare to use it because it seems that there are unsolved dependency issues.

---

