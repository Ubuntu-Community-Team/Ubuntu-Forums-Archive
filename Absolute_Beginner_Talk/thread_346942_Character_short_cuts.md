---
title: "Character short cuts"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by antiwindows798 on 2007-01-26
In Windows, when I type Ctrl + Alt + 5 I get the Euro sign. Ctrl + Alt + C gives me the copyright symbol, and so on.

In Ubuntu, no matter what combination I try out, nothing works. What are the combinations? (Without having to type in ASCI values) or if there aren't, how to set up them?

---

### Post by citizenofnowhere on 2007-01-26
I think this should answer all of your questions:

[http://www.ubuntugeek.com/special-characters-made-easier-in-ubuntu.html](http://www.ubuntugeek.com/special-characters-made-easier-in-ubuntu.html)

Have fun!

---

### Post by antiwindows798 on 2007-01-26
That's for you help, but in regard to Ubuntu, that's retarded.

Why in the world would there be a Euro sign on the "5" key? Why would anyone put it there? Because that's one of the buttons that you should press in order to get the Euro sign. I'm not supposed to learn new key combinations all over again? And let me guess, in another Linux distro I will have to learn other key combinations as well?

I'm currently trying Ubuntu out, the purpose of that is to see if is suitable for my organization. Because of some issues, I can't employ FreeBSD, so I'm checking out Linux now and I'm definitely not going to employ some noob operating system in my organization. There should be standards, and this is the billionth disappointment I have witnessed from Ubuntu in one week of time.

As far as the character short cuts go, this is what Ubuntu must be able to recognize:

Copyright notice: Ctrl + Alt + C
Registered notice: Ctrl + Alt + R
Euro sign: Ctrl + Alt + 5

...and so on. Why those character combinations? First of all, Ctrl + 5 means something else in an IDE, for example. RightWin + C + (like destribed on that page) is simply retarded, there shouldn't be a "RightWin" or "LeftWin" "button"  in the first place. When I click on the "Win" button, the "Applications" menu (or the "Places" or "System" menu) in the Gnome desktop should be actived. Why? Because you should be able to operate your OS without a mouse (how to do that in Ubuntu anyways?).

---

### Post by citizenofnowhere on 2007-01-26
Hey, I didn't make the keyboard associations.

For what it's worth I agree that there should be a standard, but ctrl+alt are modifiers used for a lot of applications on linux systems. They've been there a long time. Comparing the way Windows and Linux do things isn't going to help much either, there are things that make more sense on both systems.

That being said, if you really want ctrl + alt + 5 then use the tool mentioned in the link above and check "right alt" and "right ctrl".

You can configure your keyboard to control your desktop without using a mouse (there's an option somewhere in keyboard settings that will allow you to control your mouse with arrow keys even). You can map any key combination to any given command-line argument using xbindkeys. There is a useful gui that comes with that.

But everything is an adjustment -there will always be a learning curve.  That's all I'm going to say on the subject or I'll start a flame thread. :)

---

### Post by antiwindows798 on 2007-01-26
> Hey, I didn't make the keyboard associations.

That's why I have said: "That's for you help, but in regard to Ubuntu, that's retarded."

> For what it's worth I agree that there should be a standard, but ctrl+alt are modifiers used for a lot of applications on linux systems. They've been there a long time. Comparing the way Windows and Linux do things isn't going to help much either, there are things that make more sense on both systems.

Hmmm, actually, no. You drive Ford and Volkswagen cars the same way, right? So character shortcuts should be the same in every operating system. Ctrl + Shift + C should also be fine, Alt + Shift + C is also fine with me, anything else shows that Ubuntu/Linux is simple not ready to be taken serious for business purposes.

> That being said, if you really want ctrl + alt + 5 then use the tool mentioned in the link above and check "right alt" and "right ctrl".

Doesn't work.

> You can configure your keyboard to control your desktop without using a mouse (there's an option somewhere in keyboard settings that will allow you to control your mouse with arrow keys even). You can map any key combination to any given command-line argument using xbindkeys. There is a useful gui that comes with that.

There is seriously no way I can control my desktop with my keyboard without configuring it first with a mouse? Hmmm, Ubuntu/Linux is really starting to get on my nerves now.

> But everything is an adjustment -there will always be a learning curve. That's all I'm going to say on the subject or I'll start a flame thread.

You have been helpful, so thanks again, lol, I don't blame you for anything, I blame Ubuntu/Linux.

I disagree, sure there is a learning curve, that's acceptable, I have spend a whole week on Ubuntu and that's fine with me. But limitations are in no way acceptable and limitations have in no way anything to do with a learning curve.

I was very positive about Linux and I was even ready to help the Linux community by co-developing the codes, but like I have said, Ubuntu is getting on my nerves.

I have already replaced Microsoft Office and Internet Explorer with OpenOffice.org and Firefox in my organization, and I have encouraged some of my partners to do the same and they did. I was planning to do the same with Windows, but after getting into Ubuntu, I'm started to think that Windows is (unfortunately) superior to Linux.

FreeBSD failed on me before. If Ubuntu will fail on me now, I guess I will have to check out Solaris or Mac OS instead. Guess I will have then to do some explaining at work why Linux isn't cut for business purposes.

---

### Post by jkeyes0 on 2007-01-26
I think this site will help with the reason "X is not working like it does in Windows".

[http://linux.oneandoneis2.org/LNW1.htm]("http://linux.oneandoneis2.org/LNW1.htm")

---

### Post by citizenofnowhere on 2007-01-26
Well I sincerely hope you find somethin that suits your needs. 

FreeBSD doesn't even try to cater to desktop users, I'm sorry that had to be the first option :)

I didn't like the new Fedora because it didn't like my wireless card and that was that - so I get it. 

Have you thought about the KDE version of Ubuntu? KDE is a lot more configurable, lots of people prefer it.

If you're not going to run a heavy load server - just office stuff - try out PCLOS - great hardware support, great forums, KDE base with a unique control applet. OpenSUSE is another one to watch out for. It's extremely polished and comes in KDE or Gnome flavours.

---

### Post by cudjoe on 2007-01-26
if you want to tweak every combinaisons, you can tweak your keyboard layout file.
I use it to get french accents on a british keyboard.

Have a look at /etc/X11/xkb/symbols files, and edit the one you use.

---

### Post by antiwindows798 on 2007-01-26
> **jkeyes0 said:**
> I think this site will help with the reason "X is not working like it does in Windows".

[http://linux.oneandoneis2.org/LNW1.htm]("http://linux.oneandoneis2.org/LNW1.htm")

Hmmmm, apparently you didn't understood me: I don't care much about having to learn new things, what I do care about is limitations as in not being able to do certain things that I should be able to do. Thus in that sense I'm not only looking for a Windows "replacement"  but mainly for a Windows "alternative".

[QUOTE=citizenofnowhere]Well I sincerely hope you find somethin that suits your needs.[/QUOTE]

Wait, you are giving up already? I was rather thinking of calling up either a few of my friends (to see how it is with other Linux distros) or Ubuntu itself to bitch at them, ROFL. Seriously, having things not included is not acceptable.


[QUOTE=citizenofnowhere]FreeBSD doesn't even try to cater to desktop users, I'm sorry that had to be the first option[/QUOTE]

Yeah, I know. I was planning to use it as a web server but because of a problem with Sun, I have to choose between Linux, Solaris, Mac OS X or Windows. However, it would be nice if I could use the same OS for my desktop.

[QUOTE=citizenofnowhere]Have you thought about the KDE version of Ubuntu? KDE is a lot more configurable, lots of people prefer it.[/quote]

Yes I have thought about that but the thing is, Gnone is from GNU and GNU runs the show behind a lot of software used on Linux. So I can't just throw GNU away like that. If GNU is not able to produce a desktop, then I'm not going to trust it with other software as well.


[QUOTE=citizenofnowhere]If you're not going to run a heavy load server - just office stuff - try out PCLOS - great hardware support, great forums, KDE base with a unique control applet. OpenSUSE is another one to watch out for. It's extremely polished and comes in KDE or Gnome flavours.[QUOTE]

No, server and if possible, desktop, I need a good and well supported OS for that.

---

### Post by antiwindows798 on 2007-01-26
Hmmm,  in Layout Options you can check "Add the EuroSign to the 5 key" under "Adding the EuoSign to certain keys", and check "Press Right key to choose 3rd level" under "Third level choosers", that will enable you get the Euro sign by pressing Alt + 5. AWESOME! Except that checking either "Press Left key to choose 3rd level" in addition or " Press any of the Alt keys of choose 3rd level"  doesn't work anyone with 5. Okay, at least that's a good solution.

As for other keys, should there be a Alt + Unicode option? Like Alt + 64 to get @? And so on.

---

### Post by antiwindows798 on 2007-01-26
There is after all a good solution: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_type_extended_characters](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_type_extended_characters)

Oops, doesn't work as well, ROFL.

---

