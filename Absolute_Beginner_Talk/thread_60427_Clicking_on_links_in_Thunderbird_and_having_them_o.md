---
title: "Clicking on links in Thunderbird and having them open in Firefox [Resolved]"
date: 2005-08-27
forum: Absolute Beginner Talk
---

### Post by aysiu on 2005-08-27
I love Mozilla's Thunderbird and Firefox programs, but I have to say they haven't turned out as well in Linux for me as they have in Windows. For example, in Windows, I love how I can use the keyboard shortcut Control-1, Control-2, Control-3, etc. to go to the first, second, or third tabs, respectively. In the Linux Firefox, I have to use alt-1, alt-2, alt-3, etc., which is a little bit of a hand coordination inconvenience, as I use Control for everything else (Control-W to close a tab, Control-Tab to move to the next tab). But, you know what? That's fine.

Another inconvenience seems a bit ludicrous to me, though, and I'm wondering 1. am I the only one who's experiencing this? and 2. does anyone know if there's a fix for this?

So, here's the problem. If someone sends me a URL in an email, and I click on that URL, rather than opening up in an existing Firefox window, it opens up in a new window, *and* (more importantly), the link doesn't even open up. The new window simply displays my homepage. I Googled about it but couldn't find a solution.

I did figure out a kind of workaround--the Launchy Thunderbird extension--whereby I can right-click on the URL in the email, and in the context menu select "Launchy," and then "Open Link in Firefox," and it will open properly (old Firefox window, new tab, actual page--not my homepage). But it doesn't make sense to me that I should have to do three steps instead of one to see a page someone's emailed me.

Has this happened to anyone else? Is my computer being a freak?

---

### Post by manicka on 2005-08-27
I don't have this problem using evolution. Maybe as you suggest it is a thunderbird issue and the launchy workaround may be your only solution.

---

### Post by astoltz on 2005-08-27
My thunderbird / firefox is working like you describe - e-mail links open in a new firefox tab.  It's been a while since I've tweaked this but I think this worked for me.

edit the ~/.mozilla-thunderbird/[profile_dir]/prefs.js file and add (or change) the following:
```
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");
```Your path to firefox may be diferent.

Then, in firefox, open the advanced section of the preferences and in "Tabbed Browsing - Open links from other applications in:", select "a new tab in the most recent window".

---

### Post by aysiu on 2005-08-28
[QUOTE=astoltz]
edit the ~/.mozilla-thunderbird/[profile_dir]/prefs.js file and add (or change) the following:
```
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");
```Your path to firefox may be diferent.
[/QUOTE] Wow! Thank you so much! That was the fix. It worked! Thanks again.

---

### Post by Michael Matthews on 2005-12-31
This did not work for me. I have same problem in thunderbird and evolution.
Seems to be a firefox issue or an interface issue. Does any one know how to get firefox to open a link via cli? I used to know the netscape method but forget.
It is very annoying. Why is this broken in linux but works for windows.

---

### Post by seakiwi on 2006-01-19
[QUOTE=astoltz]My thunderbird / firefox is working like you describe - e-mail links open in a new firefox tab.  It's been a while since I've tweaked this but I think this worked for me.

edit the ~/.mozilla-thunderbird/[profile_dir]/prefs.js file and add (or change) the following:
```
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");
```Your path to firefox may be diferent.

Then, in firefox, open the advanced section of the preferences and in "Tabbed Browsing - Open links from other applications in:", select "a new tab in the most recent window".[/QUOTE]

I've been having this same problem. I tried your suggestion but for some reason I don't <B>have</B> a profile directory under ~/.mozilla-thunderbird  :confused: 

The only directory under ~/.mozilla-thunderbird is:

ht8arr8h.default

and under that are chrome, extensions. mail and US

The only reference anywhere to anything remotely related to profiles is a profile.ini file. No sign of any user.js anywhere.

Can I create one with your "fix" lines in it, and if so, where would I create it? I have no idea why I have no profile directory - although I'm using the default profile as I'm the only user, so perhaps that's why? :???:

EDIT: Never mind - I found it. Slight brain freeze moment there ;-)
One other thing though ... is there anyway to make links open in the foreground? They now open in FF OK but they open behind Thunderbird. Can I make the focus go to the link page somehow?

---

### Post by bschuteker on 2006-01-24
I am not much with the command line (yet) but I was able to accomplish this another way.
1. go to >System>preferences>preferred applications>
under browser I have firefox selected and mail reader is thunderbird (nothing in the custom)
2. I have the tab browser prefrences extension loaded in FX

Didn't have to modify anything. This worked with FX 1.0.7 and after I used Automatix to upgrade to FX 1.5 I reinstalled extensions and it works like a charm.

Mail to: links in FX also open in TB

Happy Geeking, 

Bill

---

### Post by tntc1978 on 2006-01-28
[QUOTE=bschuteker]I am not much with the command line (yet) but I was able to accomplish this another way.
1. go to >System>preferences>preferred applications>
under browser I have firefox selected and mail reader is thunderbird (nothing in the custom)
2. I have the tab browser prefrences extension loaded in FX

Didn't have to modify anything. This worked with FX 1.0.7 and after I used Automatix to upgrade to FX 1.5 I reinstalled extensions and it works like a charm.

Mail to: links in FX also open in TB

Happy Geeking, 

Bill[/QUOTE]

This worked like a charm for me too. I couldn't edit the prefs.js file, but Bills solution seems more userfriendly to me

---

### Post by disciple on 2006-02-04
the editing described by astolz worked for me..
firefox 1.5.0.1
thunderbird 1.5

---

### Post by hashimoto on 2006-02-10
[QUOTE=Michael Matthews]This did not work for me. I have same problem in thunderbird and evolution.
Seems to be a firefox issue or an interface issue. Does any one know how to get firefox to open a link via cli? I used to know the netscape method but forget.
It is very annoying. Why is this broken in linux but works for windows.[/QUOTE]

Make sure that Thunderbird (Firefox also?) is not running. If it is running the cahnges will be overwritten when the program exits. This is also said on the top of the opened .js file.

---

### Post by pebs on 2006-02-28
Try this:

[http://www.ubuntuforums.org/showpost.php?p=779054&postcount=6](http://www.ubuntuforums.org/showpost.php?p=779054&postcount=6)

Good Luck :)

---

### Post by mrklaw on 2006-03-01
the astoltz method worked for me too. Clicking on links in Thunderbird worked until I upgraded and then it broke. When I looked at my user.js file, the network.protocol-handler lines weren't even in there.

Thanks!

---

### Post by sagittarius on 2006-03-25
[QUOTE=bschuteker]1. go to >System>preferences>preferred applications>under browser I have firefox selected and mail reader is thunderbird (nothing in the custom)[/QUOTE]
is "System Preferences" available under Kbuntu? I'm running the Dapper version and it doesn't have that on the menu. 
is there another way to access it?

---

### Post by altonbr on 2006-03-25
[QUOTE=astoltz]My thunderbird / firefox is working like you describe - e-mail links open in a new firefox tab.  It's been a while since I've tweaked this but I think this worked for me.

edit the ~/.mozilla-thunderbird/[profile_dir]/prefs.js file and add (or change) the following:
```
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");
```Your path to firefox may be diferent.

Then, in firefox, open the advanced section of the preferences and in "Tabbed Browsing - Open links from other applications in:", select "a new tab in the most recent window".[/QUOTE]

**THIS WORKS GUYS**

Thunderbird 1.5.0.1
Firefox 1.5.0.1
Ubuntu 5.10

```
user_pref("network.protocol-handler.app.http", "/usr/bin/mozilla-firefox.ubuntu");
user_pref("network.protocol-handler.app.https", "/usr/bin/mozilla-firefox.ubuntu");
```

I simply had to add *.ubuntu* ast the suffix and add *mozilla-* as the prefix... all thanks to a friendly search through /usr/bin/ and a little trial and error

---

### Post by sagittarius on 2006-03-25
[QUOTE=sagittarius]is "System Preferences" available under Kbuntu? I'm running the Dapper version and it doesn't have that on the menu. 
is there another way to access it?[/QUOTE]
In answer to my own question ... yes there is. I found it under System Settings > User Account > System Settings > Default Applications.
However, even making the appropriate changes there, hasn't altered anything ... I still get Konqueror when I click on a link in a Thunderbird email. ](*,)

---

### Post by teet on 2006-03-26
[QUOTE=astoltz]My thunderbird / firefox is working like you describe - e-mail links open in a new firefox tab.  It's been a while since I've tweaked this but I think this worked for me.

edit the ~/.mozilla-thunderbird/[profile_dir]/prefs.js file and add (or change) the following:
```
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");
```Your path to firefox may be diferent.

Then, in firefox, open the advanced section of the preferences and in "Tabbed Browsing - Open links from other applications in:", select "a new tab in the most recent window".[/QUOTE]

This worked for me as well.  I'm using Firefox 1.5.0.1 and Thunderbird 1.5.  I installed Firefox 1.5 and Thunderbird 1.5 using Automatix and then upgraded to Firefox 1.5.0.1 by using the open-firefox-as-root-and-update trick.

By the way, I had to ADD these two lines, they weren't already in the prefs.js.

-teet

---

### Post by aysiu on 2006-04-18
Eight months later, the problem resurfaces. I just did a fresh Dapper install, and here comes the problem, back from the dead.

This time the prefs.js fix doesn't work.

I tried /usr/bin/firefox, firefox, mozilla-firefox, /usr/bin/mozilla-firefox, /usr/bin/mozilla-firefox.ubuntu

I tried going to System Settings and changing the default applications. I tried changing the file associations.

It's not that Konqueror opens--nothing opens. This is weird.

Any other ideas?

**Edit**: Never mind. I figured it out. First, I installed the about:config extension in Thunderbird (much easier than manually editing prefs.js files) and then I put the direct path to Firefox instead of the symlinked launcher.

---

### Post by Matthew Davidson on 2006-05-07
I think the Right Way (TM) to solve this problem is to run:

sudo update-alternatives --set x-www-browser /usr/bin/firefox

or installing the 'galternatives' package (which arguably should be in 'ubuntu-desktop') for a GUI interface to the Debian alternatives system.  See [http://www.debian-administration.org/articles/91](http://www.debian-administration.org/articles/91)

Matthew.

---

### Post by jack888 on 2006-06-04
I having trying to find a preference or system setting for this for a while.
This fix worked great 

thanks

---

### Post by t0dzilla on 2006-07-20
I've been beating my head on this one for awhile too, and the OP's post fixed it good!
Thanks for helping this to be such an excellent resource for linux users everywhere!

---

### Post by The Waco Kidd on 2006-07-20
Kudos! This has been irritating me for a while. prefs.js fixed problem straight off.

---

### Post by Ted D. on 2006-07-28
> **bschuteker said:**
> I am not much with the command line (yet) but I was able to accomplish this another way.
1. go to >System>preferences>preferred applications>
under browser I have firefox selected and mail reader is thunderbird (nothing in the custom)
2. I have the tab browser prefrences extension loaded in FX

Didn't have to modify anything. This worked with FX 1.0.7 and after I used Automatix to upgrade to FX 1.5 I reinstalled extensions and it works like a charm.

Mail to: links in FX also open in TB

Happy Geeking, 

Bill

Bill's suggestion worked for me in Dapper

Ted D.

---

### Post by jis on 2006-09-08
I am having problems with choosing default browser, too. (I am using Xubuntu, if it is relevant.) I have explained the problem in more detail [here]("http://www.ubuntuforums.org/showthread.php?p=1476533").

---

### Post by jis on 2006-09-11
> **Matthew Davidson said:**
> I think the Right Way (TM) to solve this problem is to run:

sudo update-alternatives --set x-www-browser /usr/bin/firefox

or installing the 'galternatives' package (which arguably should be in 'ubuntu-desktop') for a GUI interface to the Debian alternatives system.  See [http://www.debian-administration.org/articles/91](http://www.debian-administration.org/articles/91)

Matthew.

Thanks for telling about the Right Way (TM). It is a good way to set default browser if you want to set it for more than one application in Debian based distros. However, desktop environments, such as Xubuntu's Xfce have other means to set preferred applications.

I added /usr/bin/xfbrowser4 as a x-www-browser alternative by galternatives (which I had to install first from the Universe repository) and selected the added alternative and set status to be manual. Now I can set in the Xubuntu's 'Applications -> Settings -> Preferred Applications' dialog the preferred browser for Thunderbird and others that use x-www-browser (provided that I have not changed their preferences).

The other option would be to use Thunderbird's 'Edit -> Preferences (General tab) -> Config Editor...' to add 'xfbrowser4' to be the value of network.protocol-handler.app.http and network.protocol-handler.app.https preference. And one would somehow try to change the preferences of other applications that use x-www-browser by default, such as Gimp, too.

P.S. exo-open command works too; it selects the application by URI type of given passed command line parameter. There is some info about it in the Preferred Applications dialog's help, i.e. file:///usr/share/xfce4/doc/C/exo-preferred-applications.html.

---

### Post by hardhu on 2006-10-16
Does anybody know how (or if it is possible) to make the same when firefox is  only installed in a 32-bit chroot environment inside an amd64 kubuntu system where thunderbird is installed?
In fact if I put the path /var/chroot/usr/bin/firefox in the preferences file, when I click on a link thunderbird complains about the fact that it cannot find the real executable /usr/lib/firefox/firefox-bin, since it obviously looks in /usr/lib, not in /var/chroot/usr/lib; if I put a symlink in /usr/lib/firefox/ pointing to /var/chroot/usr/lib/firefox/firefox-bin, when I click on a link I get then an error message about incompatible libraries, because again I think thunderbird wants to load some 64bit mozilla libraries that are not compatible with 32bit firefox, so I am stuck at this point.

---

### Post by davebgimp on 2007-01-08
> user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");

I had to manually add the lines to my prefs.js file, but it solved the problem. Thanks!

---

### Post by diesel1 on 2007-03-14
Hello all,

I am running K/Ubuntu Edgy 64Bit with SwiftFox 32 bit installed.  I want to solve this issue as everything is set up and running *very* well, I have plugins and java and multimedia, but no web links from emails.

I have tried all of the steps detailed in the previous posts, but with no usable http/s links from Thunderbird.
I have Thunderbird opening SwiftFox32, but the link is not opened by SwiftFox.

I added the following to my prefs.js......


user_pref("network.protocol-handler.app.http", "/usr/bin/swiftfox_start");
user_pref("network.protocol-handler.app.https", "/usr/bin/swiftfox_start");

Could it be that I need something other than /usr/bin/swiftfox_start ?

I have trawled mozillaZine and asked there but nobody has replied.

Any help would be appreciated.

Diesel1.


EDIT: I have it fixed, I added '/opt/swiftfox/swiftfox' as the command to run!
EDIT:Now running firefox32.

---

### Post by otchie1 on 2007-03-31
2007 Thunderbird does it too. 

It's because Thunderbird uses a shortcut x-www-browser in its configs to point to the default browser instead of grabbing the system default.

Fix is as follows,

```
sudo rm -rf /etc/alternatives/x-www-browser
sudo ln -s /usr/bin/mozilla-firefox x-www-browser
```

 substitute any valid browser path instead of mozilla-firefox if you want to

---

### Post by ninjaprawn on 2007-05-22
hi

im using evolution on feisty fawn, and links do nothing! it sounds similiar to this!

ive tried every solution in here, and nothing works!

links will work properly as long as i have firefox open already, but if not, they dont open up firefox!


how can i get firefox to open when i click on a link??

---

### Post by ninjaprawn on 2007-05-22
my mistake!

i hadnt set firefox as the default browser! :)

---

### Post by altonbr on 2007-07-05
I'm shocked at Mozilla Thunderbird personally. I thought Mozilla was all about "smart and efficient" coding that only the uber-nerds would understand (I forget the adjective I'm looking for), and yet they can't seem to get an external browser (their big brother) to launch automatically?

This thread started in August 2005 and is still going on today? Mozilla needs to keep their ears open.

_Other *Mozilla Thunderbird* problems_
Print font-size: [http://ubuntuforums.org/showthread.php?t=317708](http://ubuntuforums.org/showthread.php?t=317708)

---

### Post by jis on 2007-07-05
altonbr, if you want more compact and integrated internet suite, try [SeaMonkey]("https://help.ubuntu.com/community/SeaMonkey").

---

