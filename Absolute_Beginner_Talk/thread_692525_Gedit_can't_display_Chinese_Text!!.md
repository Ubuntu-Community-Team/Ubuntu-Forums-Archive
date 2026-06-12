---
title: "Gedit can't display Chinese Text!!"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by pinkkiss110 on 2008-02-09
[SIZE="6"][COLOR="Red"]For Some weird reason! I could view the file again???????????
...Freaky ubuntu! But I love IT!!![/COLOR][/SIZE]

For some weird reason, I can type chinese character inGedit. But If I open one directly from the web, it doesn't work.

It displays something like this:
>  ¡¡¡¡ÁÚœüÐþÎäŽóµÀ²»Ô¶£¬Ò»ŽŠºìÇœœðÍßµÄ»ªÀöž®Õ¬ÄÚ£¬Ò»ÈºÈËÐÐÉ«ŽÒŽÒ£¬Ã°×ÅÃÜÃÜº®Ñ©£¬Ž©Ôœ¹ýÙŒŽóµÄÍ¥Ôº£¬¿ì²œÍùž®Û¡œÇÂäµÄÆ«ÃÅ×ßÈ¥¡£
¡¡¡µÆÁýµÄ»ð¹âÕÕÁÁÑ©µØ£¬Ò»ÐÐÈËŸ*¹ýÍ€ÌšÂ¥žó¡¢µñÁº»*¶°£¬ž÷É«Ÿ«ÖÂÐ¡ÇÉµÄÐåÐ¬£¬ÔÚ»ýÑ©ÉÏÁôÏÂÎÉÂÒµÄÐ¬Ó¡¡£



I just install ubuntu yesterday, have no linux experience...

So PLEAS&#65349;&#12288;&#65320;&#65317;&#65324;&#65328;!!!

ps. I tried to edit its option in the configuration editor. I added GB2312 under its preference/encoding/

---

### Post by phrostbyte on 2008-02-09
> **pinkkiss110 said:**
> For some weird reason, I can type chinese character inGedit. But If I open one directly from the web, it doesn't work.

It displays something like this:


I just install ubuntu yesterday, have no linux experience...

So PLEAS&#65349;&#12288;&#65320;&#65317;&#65324;&#65328;!!!

ps. I tried to edit its option in the configuration editor. I added GB2312 under its preference/encoding/

You must make sure the character encoding in gedit and in the resulting HTML file match. It is required by W3C specifications that all HTML files have a meta character encoding tag at the top.

---

### Post by alzie on 2008-02-09
Is this what you are looking for?

[http://developer.novell.com/wiki/index.php/HOWTO:_Optimise_Ubuntu_for_Chinese_desktop](http://developer.novell.com/wiki/index.php/HOWTO:_Optimise_Ubuntu_for_Chinese_desktop)

It has help for firefox as well

Good luck:)

---

### Post by pinkkiss110 on 2008-02-09
I think you misunderstood my problem? (or my discription is bad)
I don't understand. I am downloading a txt file from the web.
When i open it with gEdit it doesn't display correctly.

That's my problem...

---

### Post by alzie on 2008-02-10
I haven't been able to find any help with gedit not showing Chinese text properly.

Everything I find has to do with entering chinese characters and you can do that.  The only thing I can think of is to open text files in Open Office or to try a different text editor like leafpad (which can be installed from synaptic)

Sorry I couldn't help more

---

### Post by pinkkiss110 on 2008-02-10
> **alzie said:**
> I haven't been able to find any help with gedit not showing Chinese text properly.

Everything I find has to do with entering chinese characters and you can do that.  The only thing I can think of is to open text files in Open Office or to try a different text editor like leafpad (which can be installed from synaptic)

Sorry I couldn't help more

I with downloading a new app would solve I problem...

well I tried leafpad, and YET it still doesn't work!!!
They look Identical with random characters!!
Please Help!! Someone!!!!

---

### Post by BandD on 2008-02-10
Just for clarification, can you view Chinese Text with other files?  Are you able to imput Chinese text as well?

---

### Post by rkd on 2008-02-11
I might not be able to help, but I will try.  First a few questions.

1.  Does the problem happen with only one file that you downloaded from somewhere on the web, or does it happen with many files that you have downloaded from different web sites?

2. It might help if you attached the file to a post here in the forum so we could look at the file in hex. The option to attach a file is below the text box for entering your post, under the heading Additional Options.

3. You said that you can open gedit and enter Chinese characters. If you save the file, exit gedit, then open the file with gedit, do the Chinese characters display correctly?

4. Have you had any other problems with displaying Chinese characters on your computer?

---

