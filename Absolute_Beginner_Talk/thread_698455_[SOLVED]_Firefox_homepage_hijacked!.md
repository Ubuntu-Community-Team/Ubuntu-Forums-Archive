---
title: "[SOLVED] Firefox homepage hijacked!"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by tenjin1 on 2008-02-16
I updated Firefox yesterday through Update Manager since it was a available update. Now my home page seems to be hijacked. My homepage was set to my iGoogle homepage now when I launch firefox I see iGoogle loading then it redirects to [http://sitesure.com/?lang=en&country=us&.lang=en&.country=us&synd=ig&mid=73&ifpctok=-3788152010391156552&parent=http://www.google.com&libs=gD7mP6I5DKA/lib/libcore.js&extern_js=/extern_js/f/CgJlbhICdXMrMBA4ACwrMBI4ACwrMBM4ACw/bRftVLvRJ8A.js&prvtof=8b2VkUqfXDCVzkFMugBtMOdsFBjpDMXG6IKZY0RX]("http://sitesure.com/?lang=en&country=us&.lang=en&.country=us&synd=ig&mid=73&ifpctok=-3788152010391156552&parent=http://www.google.com&libs=gD7mP6I5DKA/lib/libcore.js&extern_js=/extern_js/f/CgJlbhICdXMrMBA4ACwrMBI4ACwrMBM4ACw/bRftVLvRJ8A.js&prvtof=8b2VkUqfXDCVzkFMugBtMOdsFBjpDMXG6IKZY0RX")
some page called suresite.com. Anyways I thought it was the firefox launcher in gdesklets where I just had to remove the %u from the launcher but my launcher command is only firefox. I've tried everything with no luck. Anyone know what to do?

---

### Post by seventhc on 2008-02-16
Have you tried opening firefox then
*Edit>Preferences>* in the Main section and ig your on igoogle then click  *Use Current Page*

---

### Post by mikeyphi on 2008-02-16
> **tenjin1 said:**
> I updated Firefox yesterday through Update Manager since it was a available update. Now my home page seems to be hijacked. My homepage was set to my iGoogle homepage now when I launch firefox I see iGoogle loading then it redirects to [http://sitesure.com/?lang=en&country=us&.lang=en&.country=us&synd=ig&mid=73&ifpctok=-3788152010391156552&parent=http://www.google.com&libs=gD7mP6I5DKA/lib/libcore.js&extern_js=/extern_js/f/CgJlbhICdXMrMBA4ACwrMBI4ACwrMBM4ACw/bRftVLvRJ8A.js&prvtof=8b2VkUqfXDCVzkFMugBtMOdsFBjpDMXG6IKZY0RX]("http://sitesure.com/?lang=en&country=us&.lang=en&.country=us&synd=ig&mid=73&ifpctok=-3788152010391156552&parent=http://www.google.com&libs=gD7mP6I5DKA/lib/libcore.js&extern_js=/extern_js/f/CgJlbhICdXMrMBA4ACwrMBI4ACwrMBM4ACw/bRftVLvRJ8A.js&prvtof=8b2VkUqfXDCVzkFMugBtMOdsFBjpDMXG6IKZY0RX")
some page called suresite.com. Anyways I thought it was the firefox launcher in gdesklets where I just had to remove the %u from the launcher but my launcher command is only firefox. I've tried everything with no luck. Anyone know what to do?

Looks as though you're correct!!
Reset to your homepage in Preferences....and delete all references to suresite!!!
If you still have the same problem after resetting your homepage - you've been hijacked.....complain to my igoogle.

---

### Post by tenjin1 on 2008-02-16
yes I have tried that an no luck. I can set my homepage to anything other than my iGoogle homepage and it doesn't redirect me to that stupid site. So this tells me it's defintely been hacked. Ive tried downgrading to a different version, re-installing, clearing data, etc with no luck. This also tells me that the problem isn't in the firefox installation but has somehow been hacked from the web.

I set my homepage to [http://www.google.com/linux]("http://www.google.com/linux"), which is working fine now for a alternative to my homepage.On the page I noticed on the top right corner I was signed into google ( which I always am so I can see my custom iGoogle homepage when I start firefox), so I signed out and went to the iGoogle homepage, which was working fine with the default iGoogle homepage, but once I signed in and it started to load my custom homepage it imediately redirected me to suresite.com. :(

---

### Post by seventhc on 2008-02-16
are you using this as the url
[http://www.google.com/ig?hl=en](http://www.google.com/ig?hl=en)
also, click on that link and see if you get redirected or does it bring you to your google page.
If it has been hijacked, I think this is the first time I've heard of this happening on linux with firefox.

---

### Post by tenjin1 on 2008-02-16
> **seventhc said:**
> are you using this as the url
[http://www.google.com/ig?hl=en](http://www.google.com/ig?hl=en)
also, click on that link and see if you get redirected or does it bring you to your google page.
If it has been hijacked, I think this is the first time I've heard of this happening on linux with firefox.

Yep that is the exact url set as my homepage, which my usrname and password are remembered so I can stay logged into so I can see my custom iGoogle homepage when I start firefox. And yes when I clicked on your link, I could see my iGoogle homepage loading and maybe after 2 seconds I was redirected to suresite.com.

---

### Post by tenjin1 on 2008-02-16
> **seventhc said:**
> 
If it has been hijacked, I think this is the first time I've heard of this happening on linux with firefox.

Yes very strange indeed that this is happening on firefox in linux!

---

### Post by Steveway on 2008-02-16
> **tenjin1 said:**
> Yep that is the exact url set as my homepage, which my usrname and password are remembered so I can stay logged into so I can see my custom iGoogle homepage when I start firefox. And yes when I clicked on your link, I could see my iGoogle homepage loading and maybe after 2 seconds I was redirected to suresite.com.

Well one of the gadgets (widgets whatever they are called) is redirecting you.
You have to find out wich it is and remove that.

---

### Post by seventhc on 2008-02-16
what happens when you go to just [http://www.google.com]("http://www.google.com/")

---

### Post by asmoore82 on 2008-02-16
temporarily create and use a new firefox profile to see if the hijack is system-wide:
Open a Terminal ("Applications -> Accessories -> Terminal"),
run ```
firefox -P
```(that 'P' must be capital)
Click "Create Profile" and go through the steps,
make sure to uncheck "Don't ask at startup,"
then highlight the new profile and click "Start Firefox."

IF the hijack is still effective in this clean firefox profile,
check to see if it is system-wide by checking the ``/etc/hosts'' file:
```
cat /etc/hosts
```
it should look something like this:
```
127.0.0.1 localhost
127.0.1.1 *<your_computer_name>*

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

IF that is clean too and the hijack persists, check for custom DNS settings on your router.

Hopefully, it's all just a small baddie on iGoogle's page.

---

### Post by wordstoliveby27 on 2008-02-16
i am a mac user and i just had this same problem...but i have found the fix.  someone on here mentioned earlier that it was a widget on your igoogle page that was redirecting you and they were totally right.  when the igoogle page would load for 2 seconds (right before the redirect) i noticed that the "this day in history" widget was displaying the suresite.com website.  what i did was i went to my igoogle page and as it was loading hit stop (right before the redirect) and then closed that widget on my igoogle homepage.  the problem has stopped and i have reset it as my homepage.

hope this helps!

---

### Post by NisKid on 2008-02-16
I use Firefox. The hack is from the gadget "This Day in History". To fix I had to use Internet Explorer go to Tools - Internet Options - Security - Restricted Sites - then hit Sites tab and add [http://sitesure.com](http://sitesure.com) and [http://www.sitesure.com](http://www.sitesure.com) 

Log into iGoogle from IE.  Once back in delete the "This Day in History" gadget. Then logout and quit IE. Restart Firefox and log back in to iGoogle. 

Before you start all this you have to be logged out of iGoogle in the first place. I had just enough time to hit log out in upper right before being transported to Sitesure.

---

### Post by nikoPSK on 2008-02-16
Just a question, so it's igoogle? Not some malicious hijack program for linux?

---

### Post by tenjin1 on 2008-02-16
> **wordstoliveby27 said:**
> i am a mac user and i just had this same problem...but i have found the fix.  someone on here mentioned earlier that it was a widget on your igoogle page that was redirecting you and they were totally right.  when the igoogle page would load for 2 seconds (right before the redirect) i noticed that the "this day in history" widget was displaying the suresite.com website.  what i did was i went to my igoogle page and as it was loading hit stop (right before the redirect) and then closed that widget on my igoogle homepage.  the problem has stopped and i have reset it as my homepage.

hope this helps!

Wow! That was it! Thx wordstoliveby! The widget "this day in history" was the one redirecting me to the that site. To fix this:** I clicked stop and removed that widget then clicked reload and no more redirecting to that site.**
I knew it couldn't have been a problem with linux or even firefox, that would just be crazy.

Thanks again to everyone who helped me with this, just goes to show that ubuntuforums is still the best place to go for support :)

---

### Post by wordstoliveby27 on 2008-02-16
no problem...i was freaking out when mine was doing the same thing.  i must give the credit to steveway though as he pointed out that it was probably a widget...

---

### Post by tenjin1 on 2008-02-16
Now I need to contact google and let them know that their widget "This day in History" seems to have the code hacked and redirecting the user to suresite.com. And who knows what the links on suresite.com front page will do, where they will take you or what they will install on your computer, as I wasn't interested in finding out :)

---

### Post by Pablo Pablovski on 2008-02-16
Check this blogger page - the suggested fix worked for me.

[http://www.schoollibraryjournal.com/blog/1340000334/post/1870021987.html?nid=3714](http://www.schoollibraryjournal.com/blog/1340000334/post/1870021987.html?nid=3714)

Edit: Sorry, I didn't read all of the thread before posting...

---

### Post by seventhc on 2008-02-16
I"m glad it wasn't something wrong with Linux :)
A lot of those widgets or all of them are done by third parties.
I think it's a *Use at your own risk* type thing

---

### Post by kriegc on 2008-02-16
> **NisKid said:**
> I use Firefox. The hack is from the gadget "This Day in History". To fix I had to use Internet Explorer go to Tools - Internet Options - Security - Restricted Sites - then hit Sites tab and add [http://sitesure.com](http://sitesure.com) and [http://www.sitesure.com](http://www.sitesure.com) 

Log into iGoogle from IE.  Once back in delete the "This Day in History" gadget. Then logout and quit IE. Restart Firefox and log back in to iGoogle. 

Before you start all this you have to be logged out of iGoogle in the first place. I had just enough time to hit log out in upper right before being transported to Sitesure.


THANK YOU.............I was going crazy trying to figure out where this piece of crap came from. Been fighting it since 8 A M .
Did a google search, found this forum, and signed up just so I could THANK YOU again.:)

---

### Post by tenjin1 on 2008-02-18
> **kriegc said:**
> THANK YOU.............I was going crazy trying to figure out where this piece of crap came from. Been fighting it since 8 A M .
Did a google search, found this forum, and signed up just so I could THANK YOU again.:)

To make it a little easier, so you don't have to mess with Internet Explorer- You can also just hit the STOP button on firefox toolbar right before it starts to redirect you to that site. Then while it's stopped, remove the widget and click RELOAD.

---

