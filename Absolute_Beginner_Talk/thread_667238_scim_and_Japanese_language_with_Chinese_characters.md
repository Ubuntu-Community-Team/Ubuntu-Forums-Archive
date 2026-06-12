---
title: "scim and Japanese language with Chinese characters"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by visionen on 2008-01-14
Hi

I installed Ubuntu yesterday on my laptop, and since I study Japanese I had to install and configure that too. I tried Scim, it did'nt work, I read about the current bug in 7.10 and the solution found here: [http://ubuntuforums.org/showpost.php?p=3676161&postcount=6](http://ubuntuforums.org/showpost.php?p=3676161&postcount=6) I followed that, but on the last step (rebooting scim manually after rebooting the computer) didnt work I just go the error message: "Fauled to Launch SCIM" though that did not seem t stop SCIM from running. Anway, writing hiragana and katakana now works, but when I try and hit space to change the word into kanji, I only get a small box with the option to change the workd to katakana, or back to hiragana. I've read about other people having this problem, but there are so many confusing bugs surrounding this program that I cant make heads or tails of how to solve it. it seems to me that Anthy doesnt load any Chinese characters at all.

I have a HP Pavillion laptop dv6000 series with amd64-bit Ubuntu 7.10

---

### Post by TWO on 2008-01-14
> **visionen said:**
> Hi

I installed Ubuntu yesterday on my laptop, and since I study Japanese I had to install and configure that too. I tried Scim, it did'nt work, I read about the current bug in 7.10 and the solution found here: [http://ubuntuforums.org/showpost.php?p=3676161&postcount=6](http://ubuntuforums.org/showpost.php?p=3676161&postcount=6) I followed that, but on the last step (rebooting scim manually after rebooting the computer) didnt work I just go the error message: "Fauled to Launch SCIM" though that did not seem t stop SCIM from running. Anway, writing hiragana and katakana now works, but when I try and hit space to change the word into kanji, I only get a small box with the option to change the workd to katakana, or back to hiragana. I've read about other people having this problem, but there are so many confusing bugs surrounding this program that I cant make heads or tails of how to solve it. it seems to me that Anthy doesnt load any Chinese characters at all.

I have a HP Pavillion laptop dv6000 series with amd64-bit Ubuntu 7.10

When I first updated to Gutsy when it was officially released, SCIM never used to work for me at all no matter what I tried. I waited for a bit longer then updated again, and after following the instructions on the following page exactly, it has worked ever since. 

[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

I don't know whether you have seen the page before or not, but it's on the Ubuntu help pages and it certainly helped to get it running. I require Japanese characters as well, so it was critcal for me to get it working since I was trying to make the transition from Windows.

Hope it helps.

P.S Completely uninstall SCIM, then follow the instructions on the page.

&#38929;&#24373;&#12387;&#12390;!

---

### Post by visionen on 2008-01-14
Thanks for your reply, but it didnt work. I unistalled scim by using the following command "apt-get remove scim" I assume that completely removes scim? if it does I am clueless, I can still not use any kanji, and I am about ti give up to be honest. Scim by the way, seems to be in the need of some serious love from its developers.

---

### Post by visionen on 2008-01-14
Any help is appreciated. Can the engine that converts hiragana to kanji simply not load?

---

### Post by seshomaru samma on 2008-01-18
did you install scim-anthy?
(that's the engine that makes kanji)

---

### Post by ryukent on 2008-02-02
SCIM still has some issues to be ironed out. Try this guide:

[https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_7%2e10](https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_7%2e10)

---

