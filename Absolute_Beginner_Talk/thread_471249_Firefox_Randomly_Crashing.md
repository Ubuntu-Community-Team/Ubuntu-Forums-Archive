---
title: "Firefox Randomly Crashing"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by dylan623 on 2007-06-11
Ever since I first installed Ubuntu, Firefox would just crash out of nowhere. Often it crashed when other programs were active, but it also does it when it is the only one running. The crashes are fairly frequent, and I have had at least 5 today. I noticed that sometimes it crashes at a certain site, but at other times it doesn't make a difference. This also  happens rarely with Thunderbird.

---

### Post by locke.dragon on 2007-06-11
i can't offer any help to your problem, but i'd like to point out that i have this same problem, although not as frequently.  i've noticed that it usually crashes when i open a lot of flash sites or games.

---

### Post by KIAaze on 2007-06-11
Are you sure it's not related to certain sites?

I know I used to have that problem specifically for sites with quicktime videos before installing some add-on which launches them externally in VLC player.
And at work, where I use an older Firefox version on Debian Sarge, it seems to crash every time I try to access .asp sites as well as sites with flash videos sometimes.

I guess it's more a Firefox bug than Ubuntu bug and you should report it to them.

---

### Post by p_quarles on 2007-06-11
Dunno about that . . . I've had Flash videos crash Liferea too. It's not so frequent/annoying that I really care, but I do think it might be a Linux problem. 

That, and the fact that Windows and Mac versions of Firefox have never given me that problem.

---

### Post by dylan623 on 2007-06-11
I think it's related to certain sites, but I don't know what the specific cause. This: [http://www.somethingawful.com/d/rom-pit/nes-rad-ninja.php](http://www.somethingawful.com/d/rom-pit/nes-rad-ninja.php) is one link that crashed Firefox a few times in a row. I'll download the add-on and see if it will work.

---

### Post by veerakumar on 2007-06-11
Have more of ram or swap space

---

### Post by DBStevens on 2007-06-11
Frequently, FIrefox crashes are the result of incorrect plugin programming.

I haven't seen a Firefox crash in a long while, however I keep the number of plugins on my systems low.

---

### Post by msgyrd on 2007-06-11
I've found the easiest way to track down errors is to launch the problematic program from the command line, then let it crash.  Usually it will give some errors that you don't get to see otherwise.  Try crashing it that way and post the results.

---

### Post by p_quarles on 2007-06-11
msgyrd: That is seriously good advice.I've found error messages by accident that way before, but somehow it didn't occur to me to use that as a diagnostic tool. 

It's also a really good comeback to anyone who says that CLIs are "too complicated." There is no equivalent method in Windows.

---

### Post by dylan623 on 2007-06-11
Okay, next time I start up Firefox it will be from the CLI. It might not crash right away, but when it does I will post the results.

---

### Post by dylan623 on 2007-06-12
Firefox just crashed a minute ago, here are the results:

dylan@dylan-laptop:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x84a4988: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x84a4988: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x84a4988: NP_GetValue
GCJ PLUGIN: thread 0x84a4988: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x84a4988: NP_GetValue return
GCJ PLUGIN: thread 0x84a4988: NP_GetValue
GCJ PLUGIN: thread 0x84a4988: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x84a4988: NP_GetValue return
The application 'Gecko' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

---

### Post by p_quarles on 2007-06-12
Don't really know what most of that means, but it does seem possible that the problem is caused by an extension. 

One thing to try would be running ```
firefox -safe-mode
``` Then go back to the page it crashed on, see what happens. 

Don't have much else.

---

### Post by gigaferz on 2007-06-12
it might not help at all, but firefox has been slowing down too much,,,and I know is not my internet connection,

my solution was flock.

just copy the plugins form mozilla-firefox to flock and itll run fine and faster,

however if it keeps crashing it could be a plugin. just delete it and see what happens,,,

---

### Post by dylan623 on 2007-06-12
Well, would a list of extensions I have active help? If so, here it is:

Adblock Plus
All-in-One Sidebar
CookieSafe
Download Manager Tweak
DownThemAll!
Fasterfox
FireFTP
GetVideo
MR Tech Local Install
Neo Diggler
Paste and Go 2
Rewind/Fast Forward
Session Manager
Stealther
Tab Mix Plus
Ubuntu Forums Menu
Undo Closed Tabs Button

I'm using the default Firefox 2 theme in case you need to know. How do I find out which plug-ins like Flash Player I have installed?

---

### Post by p_quarles on 2007-06-12
Well, this could be a complete coincidence, but I have noticed that Firefox hasn't crashed once for me since I uninstalled Fasterfox. I make NO causal connection here, just reporting the facts. 

Did you ever try my suggestion to run in safe mode (i.e., without extensions)? That might give you a hint whether it's one of those.

To your other question, I don't think plugins are installed "in" Firefox the way that extensions are. FF is able to load and embed those programs when needed, but it's not attached to it.

---

### Post by dylan623 on 2007-06-12
I was thinking that might be the problem. I haven't tried safe mode yet, since I was doing something that required an extension, but I did disable unnecessary (i.e. ones I won't even noticed are gone, which was about half the list). I'll try disabling Fasterfox and tell you what happens.

---

### Post by w4ett on 2007-06-12
I had similar problems as you, but they seem to have been reduced since I installed the flashblock extension/add on.

---

### Post by dylan623 on 2007-06-12
After disabling Fasterfox I haven't had a crash yet, but I'll try that too.

---

### Post by dylan623 on 2007-06-12
It's still happening, Firefox just crashed when I reloaded the page. I just installed Stop/Reload and StumbleVideo was in the other tab.

---

### Post by p_quarles on 2007-06-12
Well, I'm out of ideas. I guess you could install Opera, Konqueror or Flock, and see if you get better results. Wish I could I offer a better solution, though.

---

### Post by dylan623 on 2007-06-12
I guess I'll just disable more extensions, since I'd rather continue with the crashing than switch to a different browser (unless I was convinced a certain other browser was good enough).

---

### Post by dylan623 on 2007-06-12
I got this message again:

dylan@dylan-laptop:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x849e408: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x849e408: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x849e408: NP_GetValue
GCJ PLUGIN: thread 0x849e408: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x849e408: NP_GetValue return
GCJ PLUGIN: thread 0x849e408: NP_GetValue
GCJ PLUGIN: thread 0x849e408: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x849e408: NP_GetValue return
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x8475b88: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x8475b88: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x8475b88: NP_GetValue
GCJ PLUGIN: thread 0x8475b88: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x8475b88: NP_GetValue return
GCJ PLUGIN: thread 0x8475b88: NP_GetValue
GCJ PLUGIN: thread 0x8475b88: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x8475b88: NP_GetValue return
The application 'Gecko' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

After a bit of searching I think it might be the graphics driver.

---

### Post by p_quarles on 2007-06-13
> **dylan623 said:**
> I guess I'll just disable more extensions, since I'd rather continue with the crashing than switch to a different browser (unless I was convinced a certain other browser was good enough).

1) You might try adding NoScript. It prevents Javascripts from loading until you allow them. IMHo, this improves FF's overall performance (but does add some work to the whole experience).

2) Even though I'm a Firefox fanboi, I actually think that Opera is its equal.

---

### Post by dylan623 on 2007-06-13
1) I have it installed, but I disabed it, I guess I'll reactivate it.

2) I used Opera for months and loved it before I moved to Ubuntu. I used Firefox for months before that. I would agree that Opera is very good, but I like Firefox much more. I just can't leave StumbleUpon, I would miss it too much. Besides, I won't use any proprietary $oftware where Free Software is more that sufficient.

---

### Post by runoverbobby on 2007-06-15
sorry to bump this... but I'm having the same problem with firefox and can't seem to find any solutions or suggestions anywhere. I don't have any extensions or add-ons, and it crashes in safe mode too. Konqueror crashes often, too. I've noticed that it happens mainly only flash sites like youtube and (gulp) myspace.

I tried this: ```
sudo kate /usr/bin/firefox
```

then adding: ```
export XLIB_SKIP_ARGB_VISUALS=1
```
to the last but one line, as suggested by [_this thread_]("http://ubuntuforums.org/showthread.php?t=426409&highlight=firefox+keeps+crashing"), but that didn't really work, either.

---

### Post by antharr on 2007-06-15
I had numerous crashes with Firefox. I decided to try SwiftFox and I haven't had any problems with crashes since. I suggest installing Automatix2 and installing SwiftFox and all the plug-ins. Worth a shot!!!!

---

### Post by runoverbobby on 2007-06-15
swiftfox has worked great for me so far (knock on wood). thanks!

---

### Post by Vuddha on 2007-06-15
I used to use Firefox and I had the same problem.

I am using Swiftfox and it crashes quite often. At least a few times a week, and I can't associate it with anything in particular, either.

I actually use Firefox (for general browsing), Opera (for university-related browsing), and Epiphany (for university-related journal research). 

Opera is excellent.

Might give Flock a go, too.

---

### Post by dylan623 on 2007-06-15
I recently found out that it is not just a Firefox problem. While Firefox crashes the most (probably because I use it the most), it also affects Konqueror (it just crashed on me). Do you think it could be a GNOME or Ubuntu problem?

---

### Post by chek2fire on 2007-06-23
I have same poblems with swiftfox and firefox i dont know why this happen.Crashes and crashes

---

### Post by Xoanan on 2007-06-23
Same here;  Tried FF, Swiftfox, Mozilla Suite and Opera.  All of them tend to time out or crash on sites that do a lot of flash or games.

Have not tried some of those suggestions yet, but perhaps altering the config file may help a bit

---

### Post by fakie_flip on 2007-07-01
I don't know exactly what it is in the user's configuration that causes the problem, but this will solve it.

mv ~/.mozilla ~/.mozilla_backup

---

### Post by juniah on 2007-11-01
I've had mozilla start to either freeze up or crash on me as well.  For me I've noticed that Im normally on the CBC Radio 3 website which uses a flash player to stream their live webcast.  I think this is why Im getting slow downs and crashing so frequently.

---

