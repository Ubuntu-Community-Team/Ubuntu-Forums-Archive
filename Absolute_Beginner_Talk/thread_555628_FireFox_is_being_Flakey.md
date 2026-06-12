---
title: "FireFox is being Flakey"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Arukas on 2007-09-20
Hello,


  I used FireFox in XP and never had problem with it before.  


  I have the options set, where firefox should open up in a new tab, but it insist on opening up in a new window.  Anyone know how to fix that?

  Also, I am trying to download some AVI files, and instead of downloading them, it'll play them.  The only option i have is to "save link as"  and it does not save the file at all.  Anyone know how to fix this problem?

-Arukas

---

### Post by w4ett on 2007-09-20
> **Arukas said:**
> Hello,


  I used FireFox in XP and never had problem with it before.  


  I have the options set, where firefox should open up in a new tab, but it insist on opening up in a new window.  Anyone know how to fix that?

  Also, I am trying to download some AVI files, and instead of downloading them, it'll play them.  The only option i have is to "save link as"  and it does not save the file at all.  Anyone know how to fix this problem?

-Arukas

Edit>Preperences>Tabs for your window/tab problem. AVI  will be in Edit>Preferences>Content>File Types>Manage

Good Luck

---

### Post by mridkash on 2007-09-20
This problem has bugged me too!

Even when I set up tab options correctly, still the problem exists. 

Best example is, when I click on any link inside a post on this forum a new window opens instead of a tab.

Here is a screenshot of the firefox prefrences.

[IMG]http://home.mridul.googlepages.com/Screenshot-FirefoxPreferences.png[/IMG]

---

### Post by w4ett on 2007-09-20
> **mridkash said:**
> This problem has bugged me too!

Even when I set up tab options correctly, still the problem exists. 

Best example is, when I click on any link inside a post on this forum a new window opens instead of a tab.

Here is a screenshot of the firefox prefrences.



You might try a reinstall or update of firefox...this might clear up the issue..if not I'd check on the firefox irc channel for a fix..
 
irc://freenode/firefox

---

### Post by funrider on 2007-09-20
somehow firefox wont save anything at all either i do "save as" or "file..save page as".......on both 32 and 64bit ff

---

### Post by bjmgryphon on 2007-09-20
If you want to control your Tabs effectively, use the Add-on (Tools-Add-ons) called [Tab Mix Plus]("https://addons.mozilla.org/en-US/firefox/addon/1122"). You can set the option to open tabs when clicking links, bookmarks, search bar, URL, etc. The native tab controls stink.
Cheers.

---

### Post by alienexplorers on 2007-09-20
If you have problems saving files check out this page:
> [http://kb.mozillazine.org/Unable_to_save_or_download_files](http://kb.mozillazine.org/Unable_to_save_or_download_files)

---

### Post by LowSky on 2007-09-20
This is a weird fix but it works for me, switch to open in new window, then swtch it back to open in tab.. this should work. I dont know why but it does.
> **mridkash said:**
> This problem has bugged me too!

Even when I set up tab options correctly, still the problem exists. 

Best example is, when I click on any link inside a post on this forum a new window opens instead of a tab.

Here is a screenshot of the firefox prefrences.

[IMG]http://home.mridul.googlepages.com/Screenshot-FirefoxPreferences.png[/IMG]

---

### Post by w4ett on 2007-09-20
> **alienexplorers said:**
> If you have problems saving files check out this page:

Good catch alien...I hadn't seen that page...gotta bookmark it :)

---

### Post by mivo on 2007-09-20
For the tabbing problem, you can also type **about:config** in the URL field, then type in **browser.link.open_newwindow**, click on the value and select "modify". Then just put in "3" (no quotation marks).

---

### Post by Arukas on 2007-09-21
Thanks, I tried that Tab Mix add on for Firefox and so far its great, i love the fact that now my book marks open up in a new page, that a nice conveinces.

-Arukas

---

### Post by mridkash on 2007-09-21
>  		For the tabbing problem, you can also type **about:config** in the URL field, then type in **browser.link.open_newwindow**, click on the value and select "modify". Then just put in "3" (no quotation marks).

Thanks Mivo, Problem solved. That value was 2 by default.

I think it should be reported as a bug or something.

---

