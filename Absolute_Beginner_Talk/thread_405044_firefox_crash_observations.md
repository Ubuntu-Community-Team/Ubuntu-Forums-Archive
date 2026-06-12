---
title: "firefox crash observations"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by futureal2032 on 2007-04-09
hi,
well.. i am not an expert on linux...i dont know any scripting either....

but i have read many threads of firefox crashing and my firefox crashes too..
so i have made some oservations..
i am going to list them here...
in the hope that it will help Ubuntu experts to find some solution for firefox.

1. When 2 or 3 tabs (or more) are open, if i try to close a tab the browser closes.
in ideal condition only the tab i want to close should close and remaining should stay open, but that does not happen.
2. Same as above scenario.. 2 different firefox windows are open and in one window 2 or 3 tabs are open. when i try to close some tab..not only that entire window closes but the other firefox window also closes.
3. If i am browsing a website where there are image galleries or image gallery links through thumbnails. when i just click on the thumbnail the browser closes. But it works fine if i right click the thumbnailed link and open it in a "new tab" or a "new window". somehow trying to open it in the same tab closes the browser.
4. Browser closes if there are more than one java applets in a page.
5. Browser closes if there i a java based slide show or animated presentation in a page and if "back" button isclicked while the slide showis running.

so far i have made these observations.
i think its possible to oslve some of the above crashes by editing the settings in firefox config (about:config).
but as  i said i am not expert ...but if someone who knows can see if changing some options in the config helps...pls let me know.

---

### Post by aysiu on 2007-04-09
If you're getting that many crashes, you probably should do [this](http://ubuntuforums.org/showthread.php?t=103930&highlight=firefox+profile).

If not, the best way to debug it is to type ```
firefox
``` in [the terminal](http://www.psychocats.net/ubuntu/terminal) and copy and paste the output (after a crash) here.

---

### Post by TheVault on 2007-04-16
> **futureal2032 said:**
> hi,
well.. i am not an expert on linux...i dont know any scripting either....

but i have read many threads of firefox crashing and my firefox crashes too..
so i have made some oservations..
i am going to list them here...
in the hope that it will help Ubuntu experts to find some solution for firefox.

1. When 2 or 3 tabs (or more) are open, if i try to close a tab the browser closes.
in ideal condition only the tab i want to close should close and remaining should stay open, but that does not happen.
2. Same as above scenario.. 2 different firefox windows are open and in one window 2 or 3 tabs are open. when i try to close some tab..not only that entire window closes but the other firefox window also closes.
3. If i am browsing a website where there are image galleries or image gallery links through thumbnails. when i just click on the thumbnail the browser closes. But it works fine if i right click the thumbnailed link and open it in a "new tab" or a "new window". somehow trying to open it in the same tab closes the browser.
4. Browser closes if there are more than one java applets in a page.
5. Browser closes if there i a java based slide show or animated presentation in a page and if "back" button isclicked while the slide showis running.

so far i have made these observations.
i think its possible to oslve some of the above crashes by editing the settings in firefox config (about:config).
but as  i said i am not expert ...but if someone who knows can see if changing some options in the config helps...pls let me know.

------------
Yeah, I to am getting similar crashes. Only thing is, I have beryl enabled, so firefox happens to fade to a black. If you ever used windows XP and your about to log out or something and your screen fades all black, it does that here in Feisty. I donno but I did the suggestion of running firefox in terminal and then seeing the results of the crash.

---

### Post by Snyper64 on 2007-06-30
It does it for all of the above statements for me too, its really annoying when it loses what part of the page you are on, especially in a forum or a product reviews page like Newegg when you restore the last session. Sorry aysiu but my profile is fine on my machine and it still happens to me. I'm thinking its some kind of memroy leak or control problem as I also have had to close Firefox due to it using 100% of my CPU and than reopening it to fix the problem.

---

