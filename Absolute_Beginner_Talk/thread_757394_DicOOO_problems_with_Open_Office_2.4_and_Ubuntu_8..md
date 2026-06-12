---
title: "DicOOO problems with Open Office 2.4 and Ubuntu 8.10"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by michael walker on 2008-04-16
Apologies if this is not the appropriate forum for this post.

When I try to install new dictionaries with the Wizards -- Install New Dictionaries feature, the document opens however when I click the Start DicOOo button the window that opens is not sized properly and thus I cannot follow through with the install.

I've included a screenshot to help with my explanation.

Is there a way to get around this bug? Any help would be great. Thanks.

-michael

---

### Post by tnl2k7 on 2008-04-17
This isn't a fix, but can't you simply resize the window by dragging the bottom right corner of the window? The size might be remembered so it'll be the same size next time you open it.

---

### Post by Cz-David on 2008-04-20
I have exactly the same problem ... I've tried to >tab< my way through the installation as I remember it from windows but no luck... i have tried this manual instalation but also no luck
```
$ sudo apt-get install myspell-cs-cz
```

---

### Post by konungursvia on 2008-04-20
i had the same issue, there is no way to resize :(

---

### Post by abh83 on 2008-04-30
I've got the exam same issue. This is very annoying. It actually makes me furious. I was hoping to fully convert to ubuntu and ditch xp but I have some very inconvenient bugs that I did not have with Gutsy.

any solutions yet? (I so don't want to use windows anymore. :()

---

### Post by moonwreath on 2008-05-02
Turn off compiz fusion and it should work.

-moonwreath-

---

### Post by Cz-David on 2008-05-02
Thanks... It works...

just type ```
metacity --replace
```
and after installation  ```
compiz --replace
```
so simple...

---

### Post by phillipbeynon on 2008-05-07
Issue: OpenOffice.org 2.4.0 DicOOo 1.8 Window size is insufficient.
Open office requires a dictionary be installed using it's wizard.
File --> Wizards --> Install New Dictionaries --> Choose "English" --> Click "Start DicOOo"
The following screen is supposed to open showing DicOOo 's first screen allowing the user to choose the language and click next; however, the window that is created is too small and renders only some of the text and does not allow the user to navigate.
Screen capture: [http://kvark.kss.si/%7Emarjan/DicOOo_ubuntu_710_OOo_230.png](http://kvark.kss.si/%7Emarjan/DicOOo_ubuntu_710_OOo_230.png)

Resolution: Disable Visual Effects. System --> Preferences --> Appearance --> Visual Effects --> None.

Conclusion: We have a bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227626](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227626)

---

