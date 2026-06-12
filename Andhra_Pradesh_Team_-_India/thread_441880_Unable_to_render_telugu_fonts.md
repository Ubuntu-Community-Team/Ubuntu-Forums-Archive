---
title: "Unable to render telugu fonts"
date: 2007-05-13
forum: Andhra Pradesh Team - India
---

### Post by Kishandr on 2007-05-13
I tried to install telugu fonts but after installing i am still unable to render the telugu fonts in ubuntu feisty i am new to linux and i tried following different tutorial on the net but still i failed to render the fonts..i installed the language packeges also and i am used this

sudo su -
cd /usr/share/fonts/truetype/ttf-telugu-fonts
wget [http://abhiomkar.googlepages.com/fonts.cache-1](http://abhiomkar.googlepages.com/fonts.cache-1)
fc-cache

found on the net

        * sudo apt-get install ttf-telugu-fonts ttf-indic-fonts language-pack-te
        * wget [http://abhiomkar.googlepages.com/fonts.cache-1](http://abhiomkar.googlepages.com/fonts.cache-1)
        * wget [http://abhiomkar.googlepages.com/fonts.cache-1.orig](http://abhiomkar.googlepages.com/fonts.cache-1.orig)
        * sudo cp fonts.cache-1 fonts.cache-1.orig /usr/share/fonts/truetype/ttf-telugu-fonts
        * fc-cache

and this 
but still i am unable to render it shows like this


&#3077;&#3112;&#3149;&#3112;&#3118;&#3119;&#3149;&#3119; &#3128;&#3074;&#3093;&#3136;&#3120;&#3149;&#3108;&#3112;&#3122;&#3137; - &#3077;&#3112;&#3149;&#3112;&#3118;&#3134;&#3098;&#3134;&#3120;&#3149;&#3119; &#3128;&#3074;&#3093;&#3136;&#3120;&#3149;&#3108;&#3112;&#3122;&#3137; - &#3093;&#3136;&#3120;&#3149;&#3108;&#3112;&#3122;&#3137;

---

### Post by abhiomkar on 2007-05-13
Hi,
Fallow these commands

```
wget [http://abhiomkar.googlepages.com/lohit_te.ttf](http://abhiomkar.googlepages.com/lohit_te.ttf)
sudo cp lohit_te.ttf /usr/share/fonts/truetype/ttf-telugu-fonts/
sudo fc-cache
```

And Restart xsession (Ctrl+Alt+Backspace) to get correct telugu rendering.

Link,
[http://abhinay.wordpress.com/2006/10/15/telugu-rendering-in-ubuntu-linux/]("http://abhinay.wordpress.com/2006/10/15/telugu-rendering-in-ubuntu-linux/")

---

### Post by Kishandr on 2007-05-13
thanks abhinay for the support it was really helpful now i am able to render in telugu and my mom can also use desktop in telugu....but i have a another problem few web sites like eenadu and sify telugu i am still not able to access the telugu can u help me with me ...i will apprecite ur help it will really helpful thanking you kishan

---

### Post by abhiomkar on 2007-05-14
Copying eenadu font to font folder works, you can read eenadu web page. But, you 'll get '**-**' symbol in between letters.

---

### Post by Kishandr on 2007-05-14
Thanks abhinay for your help...yes now i installed it under the fonts directory and now able to read it .
I have found a answer to visiting telugu sites without any problem there is this unicode conversion gateway which helps some of the indian religonal languagues to be seen with out need of any installtion and it is much more clear.... here is the link

[http://uni.medhas.org/](http://uni.medhas.org/)

I hope u can update it on your blog which can  help othersand once again thanks for your support keep up the good work.

---

### Post by abhiomkar on 2007-05-15
It is same as [Padma]("https://addons.mozilla.org/en-US/firefox/addon/873") Firefox Extension - [https://addons.mozilla.org/en-US/firefox/addon/873](https://addons.mozilla.org/en-US/firefox/addon/873)

---

### Post by lazydesi on 2008-04-19
hi Boys,

still looking for correct font for eenadu for V8.04? any ways to get rid off those bars, gaps

---

### Post by Jayadheer on 2008-12-19
> **abhiomkar said:**
> Hi,
Fallow these commands

```
wget [http://abhiomkar.googlepages.com/lohit_te.ttf](http://abhiomkar.googlepages.com/lohit_te.ttf)
sudo cp lohit_te.ttf /usr/share/fonts/truetype/ttf-telugu-fonts/
sudo fc-cache
```

And Restart xsession (Ctrl+Alt+Backspace) to get correct telugu rendering.

Link,
[http://abhinay.wordpress.com/2006/10/15/telugu-rendering-in-ubuntu-linux/]("http://abhinay.wordpress.com/2006/10/15/telugu-rendering-in-ubuntu-linux/")



I followed all the steps you suggested but still the same I am using firfox 3.05 version on ubuntu 8.10 can any one please advice me

---

### Post by aiser on 2009-12-01
:popcorn:

---

