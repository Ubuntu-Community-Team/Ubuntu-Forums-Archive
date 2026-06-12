---
title: "chinese support"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-07-19
is there any way to make ubuntu able to read chinese site like this one [http://members.tripod.com/witchawy/Utena/utenamain.html](http://members.tripod.com/witchawy/Utena/utenamain.html)
and type chinese

---

### Post by zerobinary on 2007-07-19
anyone

---

### Post by zerobinary on 2007-07-20
plz come and help

---

### Post by expatCM on 2007-07-20
How do you know this site is in Chinese?

I have just looked at the link using one computer which has full Chinese language support (simplified and traditional) and also has working scim.  The trouble is that I do not see any Chinese characters (or any other characters at all).

---

### Post by amac777 on 2007-07-20
I have Chinese fully working (both reading and typing capablity on my computer). The site linked to above appears to be traditional Chinese using Big-5 encoding, popular in Taiwan. 

I have detailed notes at home about what I do to enable Chinese support so I will edit this post later tonight but basically you need to do the following:

Add Chinese language support:
System -> Administration -> Language Support

Install the Chinese traditional fonts: (after you do this step the site above will display correctly in firefox)

```
sudo apt-get install ttf-arphic*
```

Then install a Chinese typing input method: (I prefer GCIN over SCIM because GCIN very easily supports the WuXiaMe &#28961;&#34662;&#31859; input method which is also popular in Taiwan)

```
sudo apt-get remove --purge scim*
sudo apt-get install gcin 
im-switch -s gcin 

```

alternatively you could use scim like the previous poster uses: (this might be already installed by default)

```
sudo apt-get install scim
```

In either case, you can switch between typing Chinese and English by pressing CTRL-Space. 

I hope this helps and I will update this post later when I'm at home and make sure that's all I needed to do.

EDIT: updated to add the purging of scim before installing gcim and the adding chinese language support according to my notes.

---

### Post by zerobinary on 2007-07-20
what if i want to type chinese using pin ying
still can't c that site

---

### Post by amac777 on 2007-07-20
Are you using Feisty?

I checked my notes and the only other thing I did was enable Chinese language support using:

System -> Administration -> Language Support

I have edited my above post to add that part in. 

Did you install the arphic ttf fonts? What do you see when you go to the site above? When I go to that site (either from windows or from ubuntu) the title bar is garbled characters and there is a popup box with garbled characters but everything else shows up in traditional chinese Big-5 encoding.

Also, as far as I know, both gcin and scim and support pinyin. I use gcin and its pinyin is character by character so a little slower than using pinyin in windows where nj star or windows pinyin will guess large strings of characters for you.

---

### Post by zerobinary on 2007-07-23
how do u configure gcin to pinyin 
plz help

---

### Post by zerobinary on 2007-07-23
now the problem is [http://members.tripod.com/witchawy/Utena/utenamain.html](http://members.tripod.com/witchawy/Utena/utenamain.html) 
still not working for me
wait an sec the pops up still now working otherwise it works
the pops up box i can't display Chinese need help

---

### Post by amac777 on 2007-07-24
To type Pinyin with GCIN hold down CTRL-ALT-5.

About that website, I think it has many errors and that's why the popups don't work. They don't display correctly even when I use Windows so I think it's a problem with the website not with Ubuntu.

---

### Post by zanglang on 2007-07-24
Yeah, it doesn't have the correct encoding specified. If you use Firefox, open the View menu > Character Encoding, and select Chinese Traditional.

By the way, if you're still looking to install chinese writing, check out this guide:
[https://help.ubuntu.com/community/SCIM/Chinese](https://help.ubuntu.com/community/SCIM/Chinese)

---

### Post by zerobinary on 2007-07-24
thx i can c the site in chinese 
just not their pop ups one it is chinese i want to c that pops up in chinese too instead of u know alien encoded langauge

---

### Post by zanglang on 2007-07-25
Yeah, I could read the popup text once I changed the encoding. Have you tried that? ;)

---

### Post by zerobinary on 2007-07-27
isthier a way they do this auto and banshees how can i make it chinese and japanese supportable

---

### Post by zanglang on 2007-07-28
What banshees?

Firefox should usually detect and select the correct encoding if the webpage has the right HTML metatags coded in, for example:
```
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />
```
for english. If the page doesn't follow standards you can try and help Firefox auto detect by selecting Chinese or Japanese in View > Character Encoding > Auto Detect, but at worst you'll just have to select it from More Encodings yourself.

---

### Post by tomcheng76 on 2007-07-28
&#25105;&#24819;&#25104;&#28858;&#30333;&#39340;&#29579;&#23376;, &#36319;&#21463;&#20154;&#20445;&#35703;"&#20844;&#20027;"&#27604;&#36611;, &#36996;&#26159;&#30070;"&#30333;&#39340;&#29579;&#23376;"&#22909;!
&#24456;&#26377;&#36259;&#30340;&#32178;&#31449;  Xd

---

### Post by tomcheng76 on 2007-07-28
1. apt-get install scim scim-pinyin scim-chewing scim-tables-zh scim-qtimm im-switch
2.im-switch -s scim
3.&#30331;&#20986; &#20877;&#30331;&#20837; &#23601;&#21487;&#20197;&#20351;&#29992; scim &#36664;&#20837;&#27861;

scim-setup
&#21487;&#20197;&#21034;&#38500;&#19981;&#29992;&#30340;&#36664;&#20837;&#27861;

---

### Post by zerobinary on 2007-07-28
lol 
very interesting stie for anime fan

---

### Post by zerobinary on 2007-07-28
i can typpe chinese now
is there a way to make banshee the music player to support japanese and chinese song title 
or lag

---

### Post by tomcheng76 on 2007-07-29
i dont use banshee
i just use Amarok , plus EasyTag to get CDDB data for the japanese mp3...
works well showing chinese and japanese (i dont have chinese song nearly - -)

u must use banshee ?

---

### Post by zerobinary on 2007-07-29
no

---

### Post by zerobinary on 2007-07-30
still no goal

---

### Post by dl7und on 2007-08-30
&#25105;&#29468;&#19968;&#19979;&#65306;&#20320;&#26377;&#19968;&#20123;&#27468;&#26159;&#22312;Windows&#36681;&#25104;mp3&#30340;&#65292;&#26159;&#19981;&#26159;&#65311;&#25265;&#27465;&#65292;&#21040;2007&#24180;&#65292;Windows&#32321;&#39636;&#20013;&#25991;&#29256;&#36996;&#22312;&#29992;Big5&#65292;&#31777;&#39636;&#20013;&#25991;&#29256;&#36996;&#26159;&#29992;GB&#12290;&#27604;&#36611;&#20808;&#36914;&#65292;&#22283;&#38555;&#21270;&#30340;&#20316;&#26989;&#31995;&#32113;&#29992;Unicode&#12290;&#25152;&#20197;&#65292;&#20320;&#38614;&#28982;&#21487;&#20197;&#29992;Windows&#30340;&#22806;&#25509;&#30828;&#30879;&#65292;&#25226;&#27468;copy&#21040;Linux&#31995;&#32113;&#65292;&#35731;Ubuntu&#25226;Windows&#27284;&#26696;&#31995;&#32113;&#30340;&#32232;&#30908;&#36681;&#25104;utf-8&#65292;&#20294;&#26159;&#27468;&#30340;ID3 tag&#36996;&#26159;Big5&#25110;GB...

---

### Post by funrider on 2007-08-30
the pop up says "&#35201;&#25104;&#28858;&#29579;&#23376;&#21834;", in english "need to be a prince!"

:):):):):):):)

visit my [blog]("http://tnite.com/janus"), i will post more ubuntu how-to in chinese soon, u can also ask me question thru my site.

---

### Post by zerobinary on 2007-10-30
i have installed scim but when i click on the icon i was unable to change the language output need help
plz come back and help

---

### Post by zerobinary on 2007-10-30
i have installed scim but when i click on the icon i was unable to change the language output need help
plz come back and help
any help
ur voice is important to me

---

### Post by jenhsun on 2007-10-31
[http://ubuntuforums.org/showthread.php?t=589279](http://ubuntuforums.org/showthread.php?t=589279)

Please read all this thread

---

