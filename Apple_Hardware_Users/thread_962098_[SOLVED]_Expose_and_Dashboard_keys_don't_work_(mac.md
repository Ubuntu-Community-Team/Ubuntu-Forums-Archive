---
title: "[SOLVED] Expose and Dashboard keys don't work (macbook 4.1)"
date: 2008-10-28
forum: Apple Hardware Users
---

### Post by ecormier on 2008-10-28
I hate asking questions, but I've finally been stumped beyond my own searching/linux knowledge and I need help.
I have a macbook v4.1 and I've set the keyboard up to work as it would in MacOSX (to use the function keys as function keys I have to press fn + the function key)
this is the behavior I want and so far the F1 & F2 keys work perfectly to turn up/down the brightness, F7=last track, F8=pause/play, F9=next track, F10=mute, F11=volumedown, F12=volumeup, and the eject key works (I'm using pomme)

Here's what I want....my F3 key (expose key) should start the compiz "scale" plugin and my F4 key (dashboard key) should start the compiz "widget layer" plugin.....the problem is that compiz doesn't recognize the keys at all

I even tried xev, but the keys still spit nothing out....how can a key not be sending any data at all (is it lack of support for the keyboard device at the kernel level, or is it transmitting data some other way....like a joystick dev)

this is the only outstanding thing left for me to be completely happy with my ubuntu/macbook setup (well to be totally honest this and the audio problem...which is the fact that the sound is lacking bass, but I'm willing to wait for alsa to take care of this with the missing "surround" channel)

I would think it would be easy to remap any key press....but I have no idea how to start without xev even letting me know what the keystroke is!?!

Please if anyone can help, let me know.....everything else in terms of ubuntu on macbook rocks

Eugene

---

### Post by kosumi68 on 2008-10-29
Yes, those two keys need a kernel patch in order to work. Below is one which maps the two keys to CYCLEWINDOWS and CALC, respectively. Ideally, the keys should be mapped to appropriate application launch (AL) keys, but the expose and dashboard are not defined as such upstream. Could be oversight, could be other reasons - I do not know. We might add a package to the mactel repository that maps these keys, to spare you the trouble of compiling your own kernel. Meanwhile, happy hacking.

```

diff --git a/drivers/hid/hid-input.c b/drivers/hid/hid-input.c
index 1b2e8dc..160b967 100644
--- a/drivers/hid/hid-input.c
+++ b/drivers/hid/hid-input.c
@@ -98,8 +98,8 @@ static struct hidinput_key_translation apple_fn_keys[] = {
        { KEY_BACKSPACE, KEY_DELETE },
        { KEY_F1,       KEY_BRIGHTNESSDOWN, APPLE_FLAG_FKEY },
        { KEY_F2,       KEY_BRIGHTNESSUP,   APPLE_FLAG_FKEY },
-       { KEY_F3,       KEY_FN_F5,          APPLE_FLAG_FKEY }, /* Expos<E9> */
-       { KEY_F4,       KEY_FN_F4,          APPLE_FLAG_FKEY }, /* Dashboard */
+       { KEY_F3,       KEY_CYCLEWINDOWS,   APPLE_FLAG_FKEY }, /* Expos<E9> */
+       { KEY_F4,       KEY_CALC,           APPLE_FLAG_FKEY }, /* Dashboard */
        { KEY_F5,       KEY_KBDILLUMDOWN,   APPLE_FLAG_FKEY },
        { KEY_F6,       KEY_KBDILLUMUP,     APPLE_FLAG_FKEY },
        { KEY_F7,       KEY_PREVIOUSSONG,   APPLE_FLAG_FKEY },

```

---

### Post by cyberdork33 on 2008-10-29
> **kosumi68 said:**
> We might add a package to the mactel repository that maps these keys, to spare you the trouble of compiling your own kernel. Meanwhile, happy hacking.
That sounds like a good idea, though maintenance could be a nightmare. This is something that others have for in the past as well.

---

### Post by kosumi68 on 2008-10-29
> **cyberdork33 said:**
> That sounds like a good idea, though maintenance could be a nightmare. This is something that others have for in the past as well.

Ah - but that is why Intrepid now comes with DKMS, which actually both compiles and installs the driver. The mactel dkms packages work that way. No binaries, all kernel versions and architectures supported. Neat, isn't it :-)

---

### Post by cyberdork33 on 2008-10-29
> **kosumi68 said:**
> Ah - but that is why Intrepid now comes with DKMS, which actually both compiles and installs the driver. The mactel dkms packages work that way. No binaries, all kernel versions and architectures supported. Neat, isn't it :-)
Yes that is probably best. Actually DKMS has been around, it is just that nobody used it (except the ATI proprietary drivers.)

---

### Post by kosumi68 on 2008-10-29
Ok, there is now a hid-dkms package in the mactel PPA. It maps the expose and dashboard keys to the linux keys KEY_CYCLEWINDOWS and KEY_CALC, respectively (see /usr/include/linux/input.h). On my Intrepid setup, it makes both keys appear as X event - the dashboard key even brings up the calculator :-)

Of course, mapping the keys to the approriate action is up to user space - the CYCLEWINDOWS and CALC were the closest approximations I could find. The (initially wrong) post showing the patch has been changed accordingly.

UPDATE: After installing the package, one also needs to update the ramdisk, because hid gets loaded early.
```

sudo update-initramfs -u -v -k `uname -r`

```
Then reboot, and it should be fine. Oh well, the whole solution is a bit hackish. If you accept the default keys, I can send the patch upstream, so that we eventually get rid of this long-standing problem.

Enjoy!

---

### Post by Debilski on 2008-10-29
Great, it worked at least after rebooting. But before you submit the patch upstream, tell me, is there a way to make use of F5 and F6 on MB 3,1? xev says that right now these are not mapped with any code. (Looks just like when I press the brightness keys &#8211; the only difference being that nothing happens.)
At least for F5 it would be nice to have the &#8216;normal&#8217; behaviour straight away, so I wouldn&#8217;t need to press both Fn+F5 in order to refresh. (Hmm&#8230; Where would I use F6 for?&#8230;)

---

### Post by kosumi68 on 2008-10-29
> **Debilski said:**
> Great, it worked at least after rebooting.


Nice.

> 
But before you submit the patch upstream, tell me, is there a way to make use of F5 and F6 on MB 3,1? xev says that right now these are not mapped with any code. (Looks just like when I press the brightness keys – the only difference being that nothing happens.)


I believe someone with an MB 3 would have to answer that one.

> 
At least for F5 it would be nice to have the ‘normal’ behaviour straight away, so I wouldn’t need to press both Fn+F5 in order to refresh. (Hmm… Where would I use F6 for?…)


This will not do in a general mapping setup, I am afraid. It also touches on the hot topic of FN-key or not FN key set by default; a topic that stirs emotions :-)

---

### Post by _mario_ on 2008-10-29
Hi kosumi68,

yes it works. thanks. but i'd like to add 2 suggestions:

1. would it be possible to additionally add a mapping from enter to insert (bootcamp style), just like from backspace to delete, with:
```
{ KEY_ENTER, KEY_INSERT },
```
maybe others might also need this key.

> **kosumi68 said:**
> 
UPDATE: After installing the package, one also needs to update the ramdisk, because hid gets loaded early. Then reboot, and it should be fine.
2. this approach is likely to cause new problems (and questions) after a kernel upgrade to a major version, because the module gets rebuilt after rebooting, but again isn't incorporated into the ramdisk. what about adding the option:
```
REMAKE_INITRD=y
``` to dkms.conf?

thanks in advance & ciao,
Mario

---

### Post by cyberdork33 on 2008-10-29
> **kosumi68 said:**
> This will not do in a general mapping setup, I am afraid. It also touches on the hot topic of FN-key or not FN key set by default; a topic that stirs emotions :-)

There should at least be a userspace way to change it whether it is default one way or the other...

pommed allowed a change to the config file to reverse this behavior.

---

### Post by kosumi68 on 2008-10-30
> **_mario_ said:**
> 
1. would it be possible to additionally add a mapping from enter to insert (bootcamp style), just like from backspace to delete, with:
```
{ KEY_ENTER, KEY_INSERT },
```
maybe others might also need this key.


Interesting thought, but also controversial. It is true that the insert key is the only one of the navigation keys currently not mapped. It is also true that the natural key on a full-size apple keyboard is the help key (google). It may also be confusing to some people. Here is a deal: If you start a new thread about this key, where people can try it out using the hid-dkms package (yes, I'm putting it in), and the general feeling is 'wow, good idea', then we can send it to kernel.org. Otherwise, we'll have to find another solution for the macbooks. Ok?

> 
2. this approach is likely to cause new problems (and questions) after a kernel upgrade to a major version, because the module gets rebuilt after rebooting, but again isn't incorporated into the ramdisk. what about adding the option:
```
REMAKE_INITRD=y
``` to dkms.conf?
Mario

Good catch, thanks. Incorporated and uploaded.

To everyone: if you test the Expose, Dashboard and Insert key mappings and feel comfortable with it, please send a private message with name, email and mac model; not only macbooks. Once enough people have done that, I will send a patch to kernel.org with all names listed as Tested-by. It will take some time, but at least we make sure no-one gets bitten by the change.

Cheers!

---

### Post by cyberdork33 on 2008-10-30
> **kosumi68 said:**
> Interesting thought, but also controversial. It is true that the insert key is the only one of the navigation keys currently not mapped. It is also true that the natural key on a full-size apple keyboard is the help key (google). It may also be confusing to some people. Here is a deal: If you start a new thread about this key, where people can try it out using the hid-dkms package (yes, I'm putting it in), and the general feeling is 'wow, good idea', then we can send it to kernel.org. Otherwise, we'll have to find another solution for the macbooks. Ok?
Curious exactly what this means....

It is just my personal opinion, but I would rather have a key perform the function that is actually marked on the key by default and allow the user an option to change its function via software (gnome keyboard layout options?). Having a key marked one thing and performing a completely different function is quite confusing. The only time I have argued different is in the case of things such as the help key on the full apple keyboard that is in place of Insert as it appears on most other PC keyboards. (Clear / Numlock is another case of this). There are also a few bugs on all this in launchpad where people have of course given differing opinions.

---

### Post by Debilski on 2008-10-30
I don&#8217;t know how it is with newer or older Macbooks (I guess it is different, because Apple liked to change some of the keys on the keyboard), but on the 3,1 on the Carriage Return Key there is a large sign saying Return (&#8617;) which is &#8216;Return&#8217; in xmodmap and a smaller one saying Enter (&#8965;) which should correspond to &#8216;KP_Enter&#8217; in xmodmap. So for that one it would be reasonable to somehow map it that way. Users of course could change it afterwards with xmodmap to &#8216;Insert&#8217; it they wanted to.

However there is this issue with different generations of the Macbooks having different layouts (possibly even being non-consistent throughout different languages) so in order to remap the keycodes as OS X like as possible there should be some switch which chooses the correkt MB version, I think. Is this in any way possible?

---

### Post by cyberdork33 on 2008-10-30
> **Debilski said:**
> I don&#8217;t know how it is with newer or older Macbooks (I guess it is different, because Apple liked to change some of the keys on the keyboard), but on the 3,1 on the Carriage Return Key there is a large sign saying Return (&#8617;) which is &#8216;Return&#8217; in xmodmap and a smaller one saying Enter (&#8965;) which should correspond to &#8216;KP_Enter&#8217; in xmodmap. 
Which I think you use Fn+Return to access...

Plus that marking is pretty rare around here. I think it is only on certain international models. (Were you the one on launchpad about this?)

---

### Post by Debilski on 2008-10-30
> **cyberdork33 said:**
> Which I think you use Fn+Return to access...
Yeah, unless Fn+Return yields Insert&#8230;

> **cyberdork33 said:**
> Plus that marking is pretty rare around here. I think it is only on certain international models. (Were you the one on launchpad about this?)

No. but the marking seems to be even on English models. Even with the explicit differentiation Return/Enter: [http://www.gadget.co.za/imageLib/HomePage/SeriousHardware/MacBookKeyboard.jpg](http://www.gadget.co.za/imageLib/HomePage/SeriousHardware/MacBookKeyboard.jpg) 

Just a side node; I&#8217;m pretty sure it won&#8217;t work, though: But could anyone dream of a way of making Fn+Click = RightClick. As much as I&#8216;ve got used to using one large mouse button and two finger taps for right clicks, sometimes I miss dragging a file with the right mouse button pressed.

---

### Post by kosumi68 on 2008-10-30
> **cyberdork33 said:**
> Curious exactly what this means....


So am I :-)

> 
It is just my personal opinion, but I would rather have a key perform the function that is actually marked on the key by default and allow the user an option to change its function via software (gnome keyboard layout options?). Having a key marked one thing and performing a completely different function is quite confusing. The only time I have argued different is in the case of things such as the help key on the full apple keyboard that is in place of Insert as it appears on most other PC keyboards. (Clear / Numlock is another case of this). There are also a few bugs on all this in launchpad where people have of course given differing opinions.

This argument then leads to mapping FN+Return to KEY_KPENTER, as was also suggested by Debilski.

---

### Post by cyberdork33 on 2008-10-30
> **kosumi68 said:**
> This argument then leads to mapping FN+Return to KEY_KPENTER, as was also suggested by Debilski.
OK. I thought he was saying he wanted it to act as Insert or something...

---

### Post by _alex_ on 2008-10-30
Thought I'd chime in because I've been thinking about key remapping myself lately. What I think is really missing is the ability to remap the primary *and* secondary functionality of any key, without having to recompile parts of the kernel.

I'll give you an example. I'm running a custom compiled usbhid module that maps the primary functionality of the eject key on my Macbook Pro to "Delete" and the secondary (that is fn+Eject) to "Eject". I'm a PC guy, and I like having a dedicated delete key above backspace, but note that I also can Eject CDs using (fn+Eject).

What really bothers me is that I had to compile a kernel module to get this to work (as well as fix expose and dashboard keys). The way this should really be done is as follows: The fn key should be treated just as ctrl, alt, and super. That way xmodmap could be used to map the primary and secondary functionality of *any* key.

That would also remove the necessity to patch the kernel to enable the quirks each time Apple decides to change the hardware id, because the keyboard would be treated just like any other, save for the additional xmodmap mappings for Mac keyboards. That would also mostly resolve any grudges about how fn+Enter and the "clear" key on the aluminum keyboards should work (see launchpad bickering on the latter issue ;)). Assuming the user can set their preferred behavior quite easily outside the kernel modules.

This is of course not a trivial patch to get working, and it'd be difficult to get it accepted upstream as it'd mess with a fair chunk of "stable" albeit hackish code in usbhid and hid-quirks.

P.S.: Henrik, thanks for the great work you've been doing with mactel's PPA and submitting patches upstream and to launchpad. Thanks to you Ubuntu runs better on my Macbook out of the box than it ever did on my old acer laptop :)

---

### Post by cyberdork33 on 2008-10-30
> **_alex_ said:**
> Thought I'd chime in because I've been thinking about key remapping myself lately. What I think is really missing is the ability to remap the primary *and* secondary functionality of any key, without having to recompile parts of the kernel. Oh I completely agree with that. It is ridiculous that you have to modify the kernel to make  keyboard work the way you want to.

> **_alex_ said:**
> P.S.: Henrik, thanks for the great work you've been doing with mactel's PPA and submitting patches upstream and to launchpad. Thanks to you Ubuntu runs better on my Macbook out of the box than it ever did on my old acer laptop :)

hear, hear! It is nice to have a good programmer on our side!

---

### Post by kosumi68 on 2008-10-30
> **cyberdork33 said:**
> Oh I completely agree with that. It is ridiculous that you have to modify the kernel to make  keyboard work the way you want to.


I can only "tricond" you two. Keyboard stuff is hairy, I say.

> 
hear, hear! It is nice to have a good programmer on our side!


*blushes*

---

### Post by _mario_ on 2008-10-31
Hi all,

i didn't expect that much replies for a simple suggestion...
however i'd like to explains some things:

> **_alex_ said:**
> What really bothers me is that I had to compile a kernel module to get this to work (as well as fix expose and dashboard keys). The way this should really be done is as follows: The fn key should be treated just as ctrl, alt, and super. That way xmodmap could be used to map the primary and secondary functionality of *any* key.
...
This is of course not a trivial patch to get working, and it'd be difficult to get it accepted upstream as it'd mess with a fair chunk of "stable" albeit hackish code in usbhid and hid-quirks.

in theory you're right. that would be a nice feature, but unfortunately the FN-key is not supposed to work like this. in ealier PC days this key was invented to overcome the restrictions imposed by small laptop sizes, where a full-sized keyboard wouldn't fit. thus, to stay fully compatible, the keyboard controller itself emits different scan codes with and without FN. the operating system doesn't even notice the difference. in contrast, Apple does this translation in software. as Linux is primarily a PC operating system, it's very unlikely to get userland FN key support for a few Linux on Mac users.

having that said, i think it's a good advice to look how other PC operating systems (read Windows) work on Apple hardware, i.e. what Apple does to get it to work.

> **cyberdork33 said:**
> 
The only time I have argued different is in the case of things such as the help key on the full apple keyboard that is in place of Insert as it appears on most other PC keyboards. (Clear / Numlock is another case of this).
The Help key in windows yields Insert, just what a PC user would expect. Apple simply seems to think the user doesn't need an Insert key (maybe because its software is properly designed) and gave it another function (Help) in MacOS.

> **cyberdork33 said:**
> Curious exactly what this means....
It is just my personal opinion, but I would rather have a key perform the function that is actually marked on the key by default and allow the user an option to change its function via software (gnome keyboard layout options?). Having a key marked one thing and performing a completely different function is quite confusing.
> **Debilski said:**
> I don’t know how it is with newer or older Macbooks (I guess it is different, because Apple liked to change some of the keys on the keyboard), but on the 3,1 on the Carriage Return Key there is a large sign saying Return (&#8617;) which is ‘Return’ in xmodmap and a smaller one saying Enter (&#8965;) which should correspond to ‘KP_Enter’ in xmodmap. So for that one it would be reasonable to somehow map it that way. Users of course could change it afterwards with xmodmap to ‘Insert’ it they wanted to.
In earlier days there had been a difference between Return and Enter. most PC operating systems don't really differentiate those 2 keys anymore. (has anybody ever used Return and Enter for something differently in Linux?) however, Apple always did make a difference (while at the same time not providing an Insert key). there are applications really distinguishing those 2 functions. since PC operating systems usually do not, Apple decided to map FN-Return to Insert in Windows. I personally think that's the right decision, because it's convienient for (at least) Windows on Mac users, we don't need 2 keys doing the same, and we need an Insert key which is more important than an Enter key. and as a side note: remapping FN-behaviour is not possible with xmodmap.

so we'll have to patch the kernel. maybe having a module option similar to pb_fnmode that differentiates between FN-Return being Insert or Enter might be a solution.

i can always patch the module myself. but i thought having Insert would be helpful for others too, although it isn't consistent with what is printed on the keyboard.

last but not least: thanks kosumi68 for struggling with our wishes.

ciao,
Mario

---

### Post by cyberdork33 on 2008-10-31
> **_mario_ said:**
> as Linux is primarily a PC operating system, it's very unlikely to get userland FN key support for a few Linux on Mac users.That's no way to think! I know I am treading on dangerous territory here, but Macs _ARE_ PCs... They are just very picky and temeramental ones :). Linus even uses a Mac running linux. Don't think that Macs don't matter in Linux.

> **_mario_ said:**
> having that said, i think it's a good advice to look how other PC operating systems (read Windows) work on Apple hardware, i.e. what Apple does to get it to work. while that makes sense to do, it can also be dangerous sometimes. we don't have to (or necessarily want to) do things the way apple does them.

> **_mario_ said:**
> The Help key in windows yields Insert, just what a PC user would expect. Apple simply seems to think the user doesn't need an Insert key (maybe because its software is properly designed) and gave it another function (Help) in MacOS. I fully agree with that. I actually like having help act as Insert, but for an OSX user this is a foreign concept. "Help" should do help, not insert. Situations like this are why I think it is best to have the keys perform the functions actually printed on them by default, and allow changes in userland. It is only logical that a key that says "Help" actually does something that helps the user... Think about it as if you have no preconceptions about the layout of the keyboard.

Where this gets grey is in areas like the Function keys on modern Apple Keyboards because the intended default is not so obvious.

> **_mario_ said:**
> In earlier days there had been a difference between Return and Enter. most PC operating systems don't really differentiate those 2 keys anymore. (has anybody ever used Return and Enter for something differently in Linux?) however, Apple always did make a difference (while at the same time not providing an Insert key). there are applications really distinguishing those 2 functions. since PC operating systems usually do not, Apple decided to map FN-Return to Insert in Windows. I personally think that's the right decision, because it's convienient for (at least) Windows on Mac users, we don't need 2 keys doing the same, and we need an Insert key which is more important than an Enter key. and as a side note: remapping FN-behaviour is not possible with xmodmap. while this is an excellent argument for using Fn+Return as Insert (and I will likely make my MacBook Pro do this once I get Ubuntu on it), I still don't know if that should be a default (of course the other problem with this is that nobody knows that &#8965; = Enter, and beyond that, it doesn't seem to be consistant for which keyboard actually have the symbol on the Return key). Maybe common switches like this and Help/Insert should be in the gnome keyboard config applet for Mac layouts.

---

### Post by _mario_ on 2008-10-31
> **cyberdork33 said:**
> That's no way to think! I know I am treading on dangerous territory here, but Macs _ARE_ PCs... They are just very picky and temeramental ones :). Linus even uses a Mac running linux. Don't think that Macs don't matter in Linux.
i neither tried to start a discussion whether Macs _ARE_ PCs (or vice versa), nor whether linux on Mac users are important. the point simply is: other machines handle FN-keys in hardware. only a small user group has the possibility to to it in software. so it's the most practical solution to handle this stuff inside the kernel and leave the remaining userland untouched. it's a hack. nothing else. it's just too unlikely that someone changes a lot of APIs to get this to work for a few users, even if Linus itself uses a Mac.

> **cyberdork33 said:**
> while this is an excellent argument for using Fn+Return as Insert (and I will likely make my MacBook Pro do this once I get Ubuntu on it), I still don't know if that should be a default (of course the other problem with this is that nobody knows that &#8965; = Enter, and beyond that, it doesn't seem to be consistant for which keyboard actually have the symbol on the Return key). Maybe common switches like this and Help/Insert should be in the gnome keyboard config applet for Mac layouts.
changing Help/Insert is possible in userland. the kernel should (theoretically) emit the insert keycode for this key's scan code. so we can assign an appropriate X11 symbol, right? (on the other hand this might also be done inside the kernel, as there already is a KEY_HELP constant.)

changing the FN-key behaviour cannot be done in userland, unless the kernel exports this feature (should be easy. just like /sys/module/hid/parameters/pb_fnmode).

i could write this (2nd part). however, kosumi68, what are the chances to get this upstream? or in the mactel repo? i'm asking, because i personally don't need that functionality and it's quite some work to do.

ciao,
Mario

---

### Post by cyberdork33 on 2008-10-31
> **_mario_ said:**
> i neither tried to start a discussion whether Macs _ARE_ PCs (or vice versa), nor whether linux on Mac users are important. I know you didn't... I did. You did imply that the Mac user demographic is "not important" though. I was simply trying to make the point that you are what you think you are. If you think that you will never be important, then you never will be. Trying to be optimistic.

> **_mario_ said:**
> the point simply is: other machines handle FN-keys in hardware. well understood.

> **_mario_ said:**
> only a small user group has the possibility to to it in software. so it's the most practical solution to handle this stuff inside the kernel and leave the remaining userland untouched. it's a hack. nothing else. it's just too unlikely that someone changes a lot of APIs to get this to work for a few users, even if Linus itself uses a Mac.I am not saying that it should be changed for the benefit of Mac users only (though I still believe that should be considered a key driver in itself), but rather that the way it is currently handled (in kernel) is not the best way. The idea of Linux being flexible is what drives a change to the current situation. There also used to not be WIN keys on most PC keyboards, but they work... Things evolve. If the Fn key can be treated as any normal key on the keyboard, then it should be reported in a manner that is consistant with it function regardless of whether or not the name of the key is the same as keys on other keyboards that work differently.

Please don't take things as an attack, I am simply trying to have a discussion.

---

### Post by kosumi68 on 2008-10-31
Wow, keyboard mapping discussions really *does* stir emotions, don't they. :-)

> 
i could write this (2nd part). however, kosumi68, what are the chances to get this upstream? or in the mactel repo? i'm asking, because i personally don't need that functionality and it's quite some work to do.


Regarding the FN+F3 and FN+F4, they have a history with the kernel, including the CYCLEWINDOWS suggestion. Today, function keys should be mapped to function keys, rather than to labels. The most clean patch (and Dmitry, the input maintainer, likes clean patches) is most likely to create a new function key if none of the current ones match. This might be what it eventually ends up at. In any respect, I expect a dialog about it upstream.

Regarding KP_ENTER or INSERT, it makes little sense to me, regardless of reason, to do anything different from what other operating systems do. After all, confusion is not the goal of ubuntu. I suppose the big question is: which users are most likely to switch to ubuntu: Windows or Mac users? Serving the masses might be a good idea here.

---

### Post by cyberdork33 on 2008-10-31
> **kosumi68 said:**
> Wow, keyboard mapping discussions really *does* stir emotions, don't they. :-)yes... for some reason.

> **kosumi68 said:**
> In any respect, I expect a dialog about it upstream.That's all we can really ask for at the moment.

> **kosumi68 said:**
> I suppose the big question is: which users are most likely to switch to ubuntu: Windows or Mac users? Serving the masses might be a good idea here.Well, we are talking about apple hardware here, so... Mac users I would venture to say, though there are a lot of PC-to-Mac switchers out there that are trying to put Ubuntu on their new Mac.

---

### Post by _alex_ on 2008-10-31
Hello Mario,

I have to respectfully disagree about the current kernel space handling being practical. Take a look at usbhid.c and hid-quirks.c. The quirks are locked to the hardware and become more numerous as Apple continually shuffles keys around with each release (this has lead to numerous bugs in the past, including the aluminum key numlock messing up the keyboard, because inside usbhid it was erroneously treated as a laptop keyboard).

Last Macbook revision, we had to wait several months for a patch which merely added the hardware ID to the quirks table to make it into the repos. One has to ask oneself whether this is really practical. And in my opinion it is very clearly not. It shouldn't take months to get a functioning keyboard. In addition, these kernel space hacks lead to increasingly bloated code that continually breaks working hardware when people issue a patch with erroneous assumptions (again see launchpad for dozens of bugs because of this).

The way I see it, there should be one quirk and only one quirk in the kernel, and that is to enable fn key treatment on Macs just like any other modifier key (alt, ctrl, super). If PCs have hardware handling of the fn key, then that's their loss, but to the kernel it'd just look like a keyboard that emits more keycodes and which lacks a mac-like fn key. Then in userspace we just have a "Keyboard Shortcuts" like program that lets the user map fn+delete to "Delete", fn+anything to "whatever you want" etc.) just like any other modifier key.
(It's really a hybrid program between xmodmap and keyboard shortcuts --- since you want to map modified keys to another keycode).

This would pretty much remove 90% of the code from the quirks files. And old hardware wouldn't be repeatedly broken because new mappings could be selected (manually or automatically where possible) based on the user's model (you can set keyboard layout already anyway) and stored in a configuration file.

It's in my opinion ridiculous that this hasn't been done from the get go, and has lead us down the road where one needs to patch the kernel to make a key work a certain way---this isn't a mac only problem either, as many PC keyboards come with media keys in numerous configs.

Just my thoughts,
Alex

---

### Post by cyberdork33 on 2008-10-31
That is exactly what I was thinking too. 

P.S. The Keyboard Layouts are all screwy for international keyboards too...

---

### Post by _mario_ on 2008-10-31
> **_alex_ said:**
> 
I have to respectfully disagree about the current kernel space handling being practical. ...
i aggree. you're absolutely right. such things don't belong into a kernel. (and from the point of micro-kernel construction the whole input framework doesn't belong into the kernel at all.)
practical in my previous post meant: it was easy to implement in the kernel the first time this problem appeared. (but this implemetation evolved to a tremendous hack. yes i saw it.)

however, we still have to wait until new hardware IDs have been added for the new feature (passing FN to userspace) to be enabled automatically. although a kernel parameter may solve this quickly.

in addition, other quirks are nevertheless necessary to exclude the trackpad device, for the bcm5974 to work, unless we also incorporate it. but it will need updates due to Apple regularily changing the protocol. and following your suggestion, the userspace tools have to be updated, if Apple again decides to shuffle keys around. and that's the same: a maintenance problem. nothing else. it will take some time too.

furthermore, how does that work on the "traditional" text console?

last but not least: who is going to get his hands dirty and starts the change? in the meantime, i think, it's necessary to patch the kernel until this stuff is completely moved to userspace. hopefully the kernel developers will find a solution.

> **kosumi68 said:**
> Regarding the FN+F3 and FN+F4, they have a history with the kernel, including the CYCLEWINDOWS suggestion. Today, function keys should be mapped to function keys, rather than to labels. The most clean patch (and Dmitry, the input maintainer, likes clean patches) is most likely to create a new function key if none of the current ones match. This might be what it eventually ends up at. In any respect, I expect a dialog about it upstream.
right now, those keys are mapped to KEY_FN_F5 and KEY_FN_F4 which happed to be 470 and 469. unfortunately, the X server doesn't process keycodes greater than 255. i've already tried that. the X keymap compiler complains about an invalid range... :(

> **kosumi68 said:**
> I suppose the big question is: which users are most likely to switch to ubuntu: Windows or Mac users? Serving the masses might be a good idea here.
that's a good question. i really don't know.

ciao,
Mario

---

### Post by kosumi68 on 2008-10-31
> **_mario_ said:**
> 
however, we still have to wait until new hardware IDs have been added for the new feature (passing FN to userspace) to be enabled automatically. although a kernel parameter may solve this quickly.

in addition, other quirks are nevertheless necessary to exclude the trackpad device, for the bcm5974 to work, unless we also incorporate it. but it will need updates due to Apple regularily changing the protocol. and following your suggestion, the userspace tools have to be updated, if Apple again decides to shuffle keys around. and that's the same: a maintenance problem. nothing else. it will take some time too.


This problem is partly cushioned by the ability to use dkms packages.

---

### Post by kosumi68 on 2008-11-07
Ok, this is what went upstream: [http://lkml.org/lkml/2008/11/4/128](http://lkml.org/lkml/2008/11/4/128)

The patch has been accepted into Andrew's -mm tree.

---

### Post by cyberdork33 on 2008-11-07
> **kosumi68 said:**
> Ok, this is what went upstream: [http://lkml.org/lkml/2008/11/4/128](http://lkml.org/lkml/2008/11/4/128)

The patch has been accepted into Andrew's -mm tree.
Awesome work.

---

### Post by _mario_ on 2008-11-11
> **kosumi68 said:**
> 
REMAKE_INITRD=y
Good catch, thanks. Incorporated and uploaded.

as i expected the module hasn't been rebuilt, during kernel upgrade. thus, one has to reboot twice to get it to work. maybe we should also add the AUTOINSTALL option.

ciao,
Mario

---

### Post by kosumi68 on 2008-11-11
> **_mario_ said:**
> as i expected the module hasn't been rebuilt, during kernel upgrade. thus, one has to reboot twice to get it to work. maybe we should also add the AUTOINSTALL option.

ciao,
Mario

Yes, I have thought about it too, but it requires some testing. If you were to find that it actually works well with the AUTOINSTALL option turned on, I can change it in all current dkms modules. It would also be great if you would like to join the Mactel team, so that we can harvest your improvements of the mbp_nvidia_bl module. I will also happily review the upstream patch.

---

### Post by tonyrh on 2008-12-08
Hello,

I've read the thread and installed the hid-dkms package from mactel ppa repository so when I press the dashboard key calc starts. I have configured compiz to initiate the scale plugin when I press the expose key too.
Now I have some noob questions:

- Assigning ations in compiz or guake (a nice quake-like console) to F5 or F6 keys (without pressing fn) does not work. Do you have a fix?

- How can I remap the dashboard key to something more useful than calc?

- It's possible to have the F3-F6 keys (only those, not every F-keys) act like normal function keys without pressing fn?

Thank you,
tony

---

### Post by cyberdork33 on 2008-12-08
> **tonyrh said:**
> - Assigning ations in compiz or guake (a nice quake-like console) to F5 or F6 keys (without pressing fn) does not work. Do you have a fix?

What keyboard are you using? Aren't F5 and F6 (without Fn) the keyboard brightness keys?

---

### Post by tonyrh on 2008-12-08
> **cyberdork33 said:**
> What keyboard are you using? Aren't F5 and F6 (without Fn) the keyboard brightness keys?

Sorry, forgot to mention that I have a Macbook from November 2007 (I think it's 4,1 ?) with an italian keyboard layout.

The function keys are:

F1 Brightness down
F2 Brightness up
F3 Expose
F4 Dashboard
F5
F6
F7 <<
F8 Play/Pause
F9 >>
F10 Mute
F11 Volume down
F12 Volume up

Thanks!

---

### Post by ZOMGxuan on 2009-05-14
This is broken again on Jaunty for me, because the hid-dkms package from the mactel PPA has not been updated for Jaunty yet. Could whoever is in charge please update it soon? :)

---

### Post by cyberdork33 on 2009-05-14
> **ZOMGxuan said:**
> This is broken again on Jaunty for me, because the hid-dkms package from the mactel PPA has not been updated for Jaunty yet. Could whoever is in charge please update it soon? :)
From our email discussion on the package

the following packages are obsolete on jaunty:

* hid-dkms: the kernel keycodes for F3 and F4 (Expose/Dashboard) changed to newly created
 constants that aren't currently assigned keysyms by X11.

I am not exactly sure what you have to do now to make them functional

---

### Post by Chrissss on 2009-06-03
Hello, I'm using a apple keyboard on a "non-apple" computer with Ubuntu Jaunty. Like cyberdork33 i noticed that i can't use the F3 and F4 (Expose/Dashboard) keys to control compiz. Is there a way to use these keys on jaunty without the need to install a kernel which is aimed at apple computers?

Thanks
Christoph

---

