---
title: "Chinese input Auto recognition"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Badzmiaoo on 2008-03-31
Dear All,

I Put my wife to Ubuntu (that's what a pretty hard work :) ) Now, I have an issue with Chinese input (she writes Chinese, not me, so the system is in English with Chinese input capability). 

She complains that it is not as easy to use as under windows (yeah yeah yeah), in fact, does ubuntu can recognize some expressions in Chinese? For example when I write &#20013;&#22269;, I just need to input the first character and the system will suggest both character as a possibility?

She is really missing that feature from windows XP and quite yell at me how long does it take her to write an e-mail... (as she needs to go through each character instead of typing expression/sentences).

I think I have all the canjie, quick, and other SCIM installed if this detail can help.

Second thing, when I type a character, there is some weird displays in the suggested characters, I have a kind of domino... Can someone help me out?

Thanks.

---

### Post by plmday on 2008-04-04
There's a Firefox add-on called [Fireinput]("https://addons.mozilla.org/en-US/firefox/addon/5420") which I think could help, at least make her feel at home to finish the email.

---

### Post by seshomaru samma on 2008-04-06
the domino effect means you don't have all the fonts installed
ubuntu does a pretty bad job handling chinese support, you would expect it to download all the fonts with chinese support anyway,,,
first add this repo:
```
deb http://hk.archive.ubuntu.com/ubuntu/ gutsy universe multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ gutsy universe multiverse
```
(if you don't know how i can post more detailed explanations) 
update apt and then
run this command
```
sudo apt-cache search chinese
```
then install anything that looks like a font
(again , i can post more detailed instructions)
you can also try the [fcitx input method ]("http://www.fcitx.org/main/") which is superior, i think it suggests the next characters in combinations. I use SCIM because I need Japanese , but if you don't need Japanese - go for fcitx. 
Please notice that fcitx and SCIM cannot coexist , you will need to uninstall SCIM

---

### Post by Badzmiaoo on 2008-04-07
> **plmday said:**
> There's a Firefox add-on called [Fireinput]("https://addons.mozilla.org/en-US/firefox/addon/5420") which I think could help, at least make her feel at home to finish the email.

She is using Thunderbird... :), but I am going to see if I manage to get it installed.

She also miss it badly on Pigdin... So, that's another problem, I am going to read more about seshomaru samma solution.

Should be able to work around the repo.
Will be reading for the other input solution.

Is there a way to make a come back? I mean, if I screw up? or just reinstall the SCIM?

Thanks a lot.

---

### Post by Badzmiaoo on 2008-04-07
> **Badzmiaoo said:**
> She is using Thunderbird... :), but I am going to see if I manage to get it installed.

She also miss it badly on Pigdin... So, that's another problem, I am going to read more about seshomaru samma solution.

Should be able to work around the repo.
Will be reading for the other input solution.

Is there a way to make a come back? I mean, if I screw up? or just reinstall the SCIM?

Thanks a lot.

Just read about fctix, it's a simplified Chinese input method, not sure if it also allows to find Traditionnal ones. Besides, how will my international keyboard with dead key react with it?

I finally found out that in Mac OS, the option is called "Show Associated Words", hoped it would have the same on ubuntu... :(

Thanks

---

### Post by tomcheng76 on 2008-04-07
bump
i have the same question..
i use Quick to type chinese and i really want to turn on the "associated words" features as i type so slow, haha

---

### Post by seshomaru samma on 2008-04-07
> **Badzmiaoo said:**
> Just read about fctix, it's a simplified Chinese input method, not sure if it also allows to find Traditionnal ones. Besides, how will my international keyboard with dead key react with it?

s
according to [this thread]("http://forum.ubuntu.org.cn/viewtopic.php?t=52066&sid=859c5b55f1c94cac8c00f8d73259e131") fcitx can do traditional (post number 9), but reading through it seems that most users prefer SCIM. 
I agree that some Windows input methods are superior ,for example ziguang. SCIM can sometimes predict  the next character if you give it the first letter. For example instead of typing zhongguo (&#20013;&#22269;) you can just type zhongg or zhg .

You should be able to uninstall fcitx and reinstall scim ,if you don't like it,

---

### Post by Badzmiaoo on 2008-04-07
Hey, I tried a lot of things, I uninstall SCIM and install gcin but she was still unhappy because the function was not there, Then we decided to give a try with fcitx... it did install, we have a window with the input method shown, but we can't get it to work... :( We try anything, editing some weird input files and all, but we can't get it too actually type other language than English...
Any help?

---

### Post by Badzmiaoo on 2008-04-07
Switching to Chinese interface help solved the problem, we were able to change type chinese, but still, it does not show the associated words as they described. Maybe it's a matter of input method, she use Canjie most of the time.

I think i am gonna switch to another OS just for this problem, maybe OSx.

If anybody has another solution, it would be great.

---

### Post by seshomaru samma on 2008-04-08
what is canjie? i think the associated word only comes out in the pinyin method, but i could be wrong
probably the best solution will be to post in the Ubuntu Chinese forum
you can post in simple English, or have her post in Chinese

from my (limited) experience -OSX's Chinese input system is not as good as SCIM

---

### Post by Badzmiaoo on 2008-04-08
Thanks Seshomaru samma, then we might switch back to windows... :( but I will try to have a try of the Chinese input method at a store on the last macosx to get an idea.
I am going to see if I can contact people in HK ubuntu community.

Canjie is a method that split a word in 4 parts (4 quarters 2 above 2 below) and you input key by key, it's quick and widely used in HK and other Traditionnal Chinese reading country (HK and Taiwan).

---

