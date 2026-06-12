---
title: "Chinese Study Software for Linux?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by atmartin50 on 2007-04-24
Hi all,

First off, I'm sorry if this is in the wrong forum.

I'm curious to know what software other people are using to study Chinese in Ubuntu. I had some great stuff in my Windows days, such as Wenlin, Chinese Homework Trainer, ZDT and Xuexi Zhongwen.

I just downloaded ZDT for Linux but I'm a bit unsure as to how to install it (it's a .tbz file, a file type I've never encountered as a newbie). If anyone's using ZDT out there, could you tell me how to install it on Ubuntu?

How about DimSum? I never used it on XP, but I downloaded the files for Linux; again, they are in a different file type, this time .bz2, with an accompanying .JAR file. Could anyone help me out with the installation process for this one? And what are your thoughts on DimSum as a learning tool?

It's really a bummer that Wenlin is not working in Wine (according to what I read). It is an amazing program, but I'd rather not use the XP side of my machine anytime soon.

Any thoughts or pointers would be much appreciated! Thanks in advance!

---

### Post by crispy_420 on 2007-04-24
The page for ZDT has install instructions on it.

[http://zdt.sourceforge.net/main/installation/](http://zdt.sourceforge.net/main/installation/)

Not sure how familiar with linux you are but it lists dependencies you will need. If you are new to linux and installed your own software from outside the package manager (aka synaptic), think of each dependency as part of a recipe. Without each ingredient the final product can't be created.

---

### Post by Sef on 2007-04-24
Read [How to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

Also read [Psychocat's installing software]("http://www.psychocats.net/ubuntu/installingsoftware").

---

### Post by atmartin50 on 2007-04-26
Thanks a bunch, sef,

These pages look very informative; hope this clears things up for me!

I'd still like to hear about people studying Chinese through Ubuntu...

---

### Post by kdragon on 2007-04-26
hi,i just studied chinese for 2 months :D

do you have any idea about typing chinese characters in Feisty

---

### Post by atmartin50 on 2007-04-28
Hi kdragon, 

Sorry it took me a while to get back to you. Yes, it's very easy:

1. in Synaptic, do a search for im-switch, and then install it.
2. open a Terminal window, then type
im-switch -z en_US -s scim
and then press enter. Ignore any messages about a dependency check not working. NOTE: The 'en_US' part might be different for you if English is not your default system language.
3. You will get a message saying, 'please install the package scim-qtimm. You can exit the Terminal now. Do another search in Synaptic and install scim-qtimm.
4. After you logout and log back in, you will see the IME switcher (pardon the Windows speak!) in the upper right.
5. If you want simplified Chinese input support, search for scim-pinyin in Synaptic and install it.
6. If you want traditional Chinese input support, install scim-chewing.

That's it! You should now be able to type Chinese characters! Good luck; hope this helps.

---

### Post by Brian96 on 2007-07-30
This thread seems to be about dead, but I just found an app in the repositories called "hanzim" that I really like. It is not comprehensive, but it is great for learning Chinese characters, particularly if you like analyzing the structure of each character.

The only problem I had with it is that it did not automatically install a launcher in the menu. For now I run it by hitting ALT+F2 and typing "hanzim" into the app launcher.

---

### Post by atmartin50 on 2007-07-31
Hi Brian96:

No, it's not dead yet; it's just that I've had other things going on which have hampered my Chinese studies a bit. Please let me know if you come across any other promising apps.

Yes, Hanzim seems to be a good program. I also found KVocTrain in the repositories, but I can't really figure out how it works. As a dictionary, I'll be using StarDict, but I've yet to download dictionaries from their website (oddly, they were pre-loaded and ready to go when I was using Edgy). Another one is LangDrill; however, you would need to edit the databases (via the text files) to use it to study Chinese, since it is meant to be a Japanese study tool.

One that's really worth checking out (I used it in my XP days, and according to the website, it can be used in Linux with Wine) is Teachmaster (go to [www.teachmaster.de](www.teachmaster.de)). It's a very useful tool, because in addition to having pronunciation, definition, part of speech, etc., you can also create example sentences for yourself. But I've not started using it in Ubuntu just yet.

Though I don't miss Windows a single bit, I sure do miss Wenlin and Xuexi Zhongwen.

Regards,
Aaron

---

### Post by cwmccabe on 2007-12-08
I installed Hanzim from the repositories, but I am having trouble getting it to work correctly.

I can do this:
- click on characters to view their definitions, related characters, and character components

I _cannot_ do this:
- enter text from my keyboard

When I click on the definition panels, I see the blinking cursor as though it's ready for text to be entered.  But when I type any text, no input appears.  If I click on the &#33521;&#27721;button in the upper right, a message appears at the bottom of the window saying "Please click in the English definition panel in the center and type a word or phrase."  I can click in the definition panel, but then it won't allow me to type anything in...

Has anyone else experienced this problem?  Solutions or suggestions about what I could try?

---

### Post by atmartin50 on 2007-12-09
Hi cwmccabe,

I had the same problem you described when I was running Ubuntu Edgy and Feisty. But after starting to use Xubuntu Feisty, I am suddenly able to input text in the said box. The problem is, I don't really know how to use Hanzim effectively.

Maybe you could try uninstalling and then re-installing Hanzim? I'm sure that's not much help, but it may be worth a shot...

And to any and all interested:

I recently stumbled upon a website called Clavis Sinica ([www.clavisinica.com](www.clavisinica.com)), and this software seems like a really great tool (also impressive considering that it's cross-platform). If I purchase it (at $60, it seems like a reasonable price), I'll be sure to report the results here. Has anyone else tried it out? If so, would you recommend it?

Regards,
Aaron

---

### Post by aldeby on 2008-06-17
hi cwmccabe, 
on one machine equipped with AMD processor and ATi video card I also experience this misbehavior. I managed to narrow the problem to tcl/tk. It's these libraries that all programs I cannot enter the text into have in common. It shouldn't be a hanzim bug. 

In fact on an Intel machine I'm able to enter the text. (even though only I managed to make it search only le &#20102; character... it seems it requires the exact pinyin with the tones accent. but where do I find the third accent letters?)

@ Aaron,
wenlin works flawlessly with wine. Just install it directly in linux (you should never try to run the windows setup). Give it a try!

Cheers

---

### Post by atmartin50 on 2008-06-19
Hi aldeby,

Hey, that's good to know---thanks! I'll have to procure Wenlin again, as I lost the installation file when I ditched Windoze over a year ago. Maybe a silly question, but could you say more about what you said here:
> Just install it directly in linux (you should never try to run the windows setup)
I've only used Wine a few times, and it was experimental at best.

If you could help me out, it'd be much appreciated, as Wenlin is an AWESOME tool.

Thanks,
Aaron

---

