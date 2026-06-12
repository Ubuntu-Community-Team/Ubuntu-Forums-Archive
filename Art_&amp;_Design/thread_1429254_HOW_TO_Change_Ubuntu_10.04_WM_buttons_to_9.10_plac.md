---
title: "HOW TO: Change Ubuntu 10.04 WM buttons to 9.10 placement/order"
date: 2010-03-13
forum: Art &amp; Design
---

### Post by MichaelSwengel on 2010-03-13
For now, here's how to change the maximize, minimize, close buttons to the right hand side:

```
gconftool-2 --set “/apps/metacity/general/button_layout” --type string “:maximize,minimize,close”
```


[IMG]http://captures.truesongmedia.com/d5026be92f17224f9b81fb4f94df8030.png[/IMG]

[IMG]http://captures.truesongmedia.com/c9655613c6b5a255a9b9ceb30ef5136b.png[/IMG]


If you're not using one of the 10.04 themes, you can use this to put the buttons back in the 9.10 order:
```

gconftool-2 --set “/apps/metacity/general/button_layout” --type string “:minimize,maximize,close”
```

[IMG]http://captures.truesongmedia.com/c98fba8f9ae925cb875331a9b742b199.png[/IMG]


Let's hope we have a graphical option for this in the 10.04 final release.

---

### Post by appier on 2010-03-13
Good work!  I like the looks of the new theme--just not the button on the left thing.  Given the users at my school, I definitely want to keep the buttons in the same order and same place--it will make my life just a bit easier.  I definitely agree with you on the GUI option.

Thanks,

Mark

---

### Post by MichaelSwengel on 2010-03-13
Thanks, Appier. :)

Hopefully it helps someone.

I just think the button change was an idiotic move by the art team. We've been used to the right-side buttons for years - and then they switch it up in a late alpha. Seems odd to me. ](*,)

The default needs to be the right side - with an OPTION to move the buttons to the left should the user so desire.

The 10.04 themes also make the buttons look horrible if they are rearranged (put into 9.10 order). :-(

---

### Post by durand on 2010-03-14
I think the string should be menu:minimize,maximize,close to accomodate the window icon.

---

### Post by pastalavista on 2010-03-14
> **MichaelSwengel said:**
> 

Let's hope we have a graphical option for this in the 10.04 final release.

There is a graphical solution already in the newest [Ubuntu-Tweak]("http://ubuntu-tweak.com/")

---

### Post by MichaelSwengel on 2010-03-14
> **pastalavista said:**
> There is a graphical solution already in the newest [Ubuntu-Tweak]("http://ubuntu-tweak.com/")


That's great - but it needs to be built in to the OS.

---

### Post by MichaelSwengel on 2010-03-14
> **durand said:**
> I think the string should be menu:minimize,maximize,close to accomodate the window icon.


That's true, you can do that too. :)

---

### Post by pastalavista on 2010-03-14
> **MichaelSwengel said:**
> That's great - but it needs to be built in to the OS.

no it doesn't need to be, you just want it to be

---

### Post by MichaelSwengel on 2010-03-14
> **pastalavista said:**
> no it doesn't need to be, you just want it to be

It's a key option for users. So absolutely I want it to be.

Something this basic should not require users to download Ubuntu-Tweak.

---

### Post by pastalavista on 2010-03-14
> **MichaelSwengel said:**
> It's a key option for users. So absolutely I want it to be.

Something this basic should not require users to download Ubuntu-Tweak.

Well, Microsoft and Apple disagree with you. They make a LOT of money selling systems that can't do what you want.

---

### Post by MichaelSwengel on 2010-03-14
> **pastalavista said:**
> Well, Microsoft and Apple disagree with you. They make a LOT of money selling systems that can't do what you want.

I don't give a crud what MS and Apple think!

Linux is meant to be customizable by the user. A key reason users switch to Linux is to get away from the restrictions of MS and Apple.

---

### Post by pastalavista on 2010-03-14
> **MichaelSwengel said:**
> 
Linux is meant to be customizable by the user.

It is customizable via command-line. Somebody will soon add an app to gnome that will do it, because it isn't that difficult. Make your suggestion to Canonical or Gnome. You may get it in an upcoming release or even an update (since Lucid is an LTS release). That would likely never happen in commercial OS's.

---

### Post by MichaelSwengel on 2010-03-14
> **pastalavista said:**
> It is customizable via command-line. Somebody will soon add an app to gnome that will do it, because it isn't that difficult. Make your suggestion to Canonical or Gnome. You may get it in an upcoming release or even an update (since Lucid is an LTS release). That would likely never happen in commercial OS's.

And this is the fundamental problem with which Linux has been plagued.

If it is to be adopted by the masses, the user needs a graphical means for customization built in to the OS itself.

This suggestion has already been made to Canonical. This is not a GNOME issue. It's an Ubuntu configuration issue.

THIS thread is merely a How-to for those who want to move the buttons.

If you disagree with the premise thereof, why are you on this thread?

---

### Post by pastalavista on 2010-03-14
> **MichaelSwengel said:**
> And this is the fundamental problem with which Linux has been plagued.

If it is to be adopted by the masses, the user needs a graphical means for customization built in to the OS itself.

This suggestion has already been made to Canonical. This is not a GNOME issue. It's an Ubuntu configuration issue.

THIS thread is merely a How-to for those who want to move the buttons.

If you disagree with the premise thereof, why are you on this thread?

I just wanted to tell you about Ubuntu Tweak. So you wouldn't be so disillusioned about Ubuntu. and...

I am a child of the universe
no less than the trees and the stars
I have a right to be here

---

### Post by pastalavista on 2010-03-14
PS... besides the command line method described above, you can do the same thing in gconf-editor, but you still have to edit some text want to know how?

---

### Post by MichaelSwengel on 2010-03-14
> **pastalavista said:**
> I just wanted to tell you about Ubuntu Tweak. So you wouldn't be so disillusioned about Ubuntu. and...

I am a child of the universe
no less than the trees and the stars
I have a right to be here

I don't think anyone here is disillusioned with Ubuntu... :rolleyes:

...just a little frustrated that the art team pulled this change in a late alpha just before the UI freeze. Ubuntu Tweak doesn't change their decision.

No one is questioning anyone's *right* to be here.

---

### Post by MichaelSwengel on 2010-03-14
> **pastalavista said:**
> PS... besides the command line method described above, you can do the same thing in gconf-editor, but you still have to edit some text want to know how?

It's really more of a pain to go that route than to paste in a line of code unfortunately.  (If it's the way I'm thinking, that is.)

---

### Post by pastalavista on 2010-03-14
> **MichaelSwengel said:**
> It's really more of a pain to go that route than to paste in a line of code unfortunately.  (If it's the way I'm thinking, that is.)
The gconf-editor method is easier for me to remember. Do you have it in your Applications menu. It can be added (if it isn't there already) in Applications/System Tools/Configuration Editor. Or just run with Alt-F2 'gconf-editor'.

Open Apps/Metacity/General and edit the button_layout key. The colon is the middle of the toolbar so just put the window manage entries to the right of the colon and menu to the left of it and you can arrange the buttons in any order you want... just by moving the text in relation to the colon.

---

### Post by MichaelSwengel on 2010-03-14
> **pastalavista said:**
> The gconf-editor method is easier for me to remember. Do you have it in your Applications menu. It can be added (if it isn't there already) in Applications/System Tools/Configuration Editor. Or just run with Alt-F2 'gconf-editor'.

Open Apps/Metacity/General and edit the button_layout key. The colon is the middle of the toolbar so just put the window manage entries to the right of the colon and menu to the left of it and you can arrange the buttons in any order you want... just by moving the text in relation to the colon.

Yeah, that's the way I was thinking.

It's really easier to just paste a line into Terminal. (Good thinking though)

---

### Post by pastalavista on 2010-03-14
> **MichaelSwengel said:**
> Yeah, that's the way I was thinking.

It's really easier to just paste a line into Terminal. (Good thinking though)
yeah.. it is easier to paste a line if you have it handy to copy, but if you don't and don't want to search for it, AND you aren't well versed in CLI enough to remember it all (like me), gconf-editor is the way to go.

---

### Post by MichaelSwengel on 2010-03-14
> **pastalavista said:**
> yeah.. it is easier to paste a line if you have it handy to copy, but if you don't and don't want to search for it, AND you aren't well versed in CLI enough to remember it all (like me), gconf-editor is the way to go.

True. :)

Still, I hope the devs get smart and add a checkbox or something of that sort to the Appearance menu.

---

### Post by appier on 2010-03-15
> **MichaelSwengel said:**
> ...add a checkbox or something of that sort to the Appearance menu.

I agree with you on this one.  I am not looking forward to the "Where did my window/term paper/important spreadsheet go?" type of questions which already occur when under serious time pressure.  So, for now, any computers with the new LTS distribution here will feature buttons on the right.

I hope the devs listen to the community, revert the default position of the buttons back to the upstream Gnome position, and then place the new button order as a prominent option.  If the new button arrangement truly is more efficient, make it the default on the next regular release so our "less computer savvy" users can adjust before the next LTS.

---

### Post by keypox on 2010-03-18
> **pastalavista said:**
> The gconf-editor method is easier for me to remember. Do you have it in your Applications menu. It can be added (if it isn't there already) in Applications/System Tools/Configuration Editor. Or just run with Alt-F2 'gconf-editor'.

Open Apps/Metacity/General and edit the button_layout key. The colon is the middle of the toolbar so just put the window manage entries to the right of the colon and menu to the left of it and you can arrange the buttons in any order you want... just by moving the text in relation to the colon.

thanks ubuntu-tweak wasnt working...

---

### Post by warparty on 2010-03-20
Now I understand that most market driven interactive products go through a series of checks and balances before "perfection" is reached.  And no one designer can be blamed or have absolute control.  BUT WTF.  Common sense tells us not to stare at the sun, AND NOT TO PUT THE EXIT BUTTON NEXT TO THE EDIT MENU.

Ubuntu team, you know me :cool:, I love you guys.  Just don't mess with my default interface and color contrast,  that's all. <3

---

### Post by airtonix on 2010-03-20
> **MichaelSwengel said:**
> 
Let's hope we have a graphical option for this in the 10.04 final release.

1. alt-f2
2. gconf-editor
3. apps/metacity/general/button_layout
4. ????
5. profit.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=150820&stc=1&d=1269130020[/IMG]

---

### Post by Slim Odds on 2010-03-21
Moving the WM buttons **BY DEFAULT **is an **ABSOLUTELY HORRIBLE** idea.

A distant second is that **ugly** new default color scheme.

Both of which **MUST BE CHANGED** _immediately_ after installing.

I've always been a huge fan of Ubuntu, but these two idiotic changes have really got me questioning Canonial.

They put together this solid and useful OS and then do something so insanely stupid as this.

What _**were**_ you thinking?

---

### Post by Spr0k3t on 2010-03-25
I have to agree with the idea where the upstream of Gnome layout/design should be kept.  However, I believe there should be some method that allows better (sic/easier) customization for those who are not so savvy with Linux in general.  I've seen many people convert over to Linux of some flavor going irate when they try to go back to their prior OS.  Sometimes it's the small things that cause disasters... the proverbial butterfly flapping its wings if you will.  Me personally... I'd love to have the close button on the left like I had it in the good ol' days of Workbench.  Times change and standards come from change.  Change is good.  It is a constant.

---

### Post by Slim Odds on 2010-03-25
> **Spr0k3t said:**
> ... Change is good....

Sorry, but that's not always true. Change can be good or BAD.

This is a BAD change that has many downsides as some have mentions. It's not the fact of change that I don't like, it's the type of change.

A) There is no reason to change the default behavior. There is no benefit to the change.
B) There are many negatives about the change (missing icon, clutter with menus, left side overload, different for no reason, etc).

All bad, none good.

---

### Post by anechoic on 2010-04-03
> **MichaelSwengel said:**
> It's a key option for users. So absolutely I want it to be.

Something this basic should not require users to download Ubuntu-Tweak.

Tweak and gfconfig are just front ends for what's 'under the hood' - you could also make these tweaks using the command line

---

### Post by anechoic on 2010-04-03
> **Slim Odds said:**
> Moving the WM buttons **BY DEFAULT **is an **ABSOLUTELY HORRIBLE** idea.

A distant second is that **ugly** new default color scheme.

Both of which **MUST BE CHANGED** _immediately_ after installing.

I've always been a huge fan of Ubuntu, but these two idiotic changes have really got me questioning Canonial.

They put together this solid and useful OS and then do something so insanely stupid as this.

What _**were**_ you thinking?

the beautiful thing about Linux is that you can set up things as you like them...
there is no need to settle for what aesthetically challenged software managers hoist onto the public ;)

---

### Post by dnairb on 2010-04-03
> **MichaelSwengel said:**
> That's great - but it needs to be built in to the OS.

If the change is made permanent, there must be an option, that can be found easily, for the user to change it back. if there is to be no such option available, then the buttons should be left as they are in 9.10, i.e. on the right.

I know that the button position can be changed via command line or gconf-editor, but how many users actually know this without reading threads like this? Indeed this can be done in Jaunty, and maybe earlier versions. I wouldn't have known that it was possible if the devs hadn't decided on this change. So at least one good thing has come of this, I guess.

---

### Post by durand on 2010-04-03
> **dnairb said:**
> If the change is made permanent, there must be an option, that can be found easily, for the user to change it back. if there is to be no such option available, then the buttons should be left as they are in 9.10, i.e. on the right.

I know that the button position can be changed via command line or gconf-editor, but how many users actually know this without reading threads like this? Indeed this can be done in Jaunty, and maybe earlier versions. I wouldn't have known that it was possible if the devs hadn't decided on this change. So at least one good thing has come of this, I guess.

Exactly what I was going to say!

---

### Post by anechoic on 2010-04-03
> **dnairb said:**
> If the change is made permanent, there must be an option, that can be found easily, for the user to change it back. if there is to be no such option available, then the buttons should be left as they are in 9.10, i.e. on the right.

I know that the button position can be changed via command line or gconf-editor, but how many users actually know this without reading threads like this? Indeed this can be done in Jaunty, and maybe earlier versions. I wouldn't have known that it was possible if the devs hadn't decided on this change. So at least one good thing has come of this, I guess.

then I would suggest using an OS that can't be changed easily under-the-hood...the great thing about Linux is that you can customize everything about it to your liking by using tools like gconf editor and ubuntu tweak
:)

---

### Post by durand on 2010-04-03
> **anechoic said:**
> then I would suggest using an OS that can't be changed easily under-the-hood...the great thing about Linux is that you can customize everything about it to your liking by using tools like gconf editor and ubuntu tweak
:)

That's not the point. It's great being able to customise everything, but that feature is pointless unless people know about it, and the best way to do that is to make it obvious, especially to new users.

---

### Post by Slim Odds on 2010-04-03
> **durand said:**
> That's not the point. It's great being able to customise everything, but that feature is pointless unless people know about it, and the best way to do that is to make it obvious, especially to new users.

Exactly!!

Having idiotic defaults that MUST be changed, even if it was trivial (and, unfortunately, it's not) is just plain dumb.

As has been mentioned already (many times), the new defaults are terrible for many reasons. They create a major overload on the left side of the window (including being too close to the menu so that accidental mis-clicks are more likely) . The buttons are NOT in the normal order, so that creates more confusion. The program icon is removed from the upper left corner (not a huge issue, but it is nice to have that visual clue when your eyes scan the display).

And yet there is not ONE single benefit that I've heard mentioned (except maybe "change", as if that's automatically a good thing).

The "change" is all BAD and not any good.

---

### Post by anechoic on 2010-04-03
> **Slim Odds said:**
> Exactly!!

Having idiotic defaults that MUST be changed, even if it was trivial (and, unfortunately, it's not) is just plain dumb.

As has been mentioned already (many times), the new defaults are terrible for many reasons. They create a major overload on the left side of the window (including being too close to the menu so that accidental mis-clicks are more likely) . The buttons are NOT in the normal order, so that creates more confusion. The program icon is removed from the upper left corner (not a huge issue, but it is nice to have that visual clue when your eyes scan the display).

And yet there is not ONE single benefit that I've heard mentioned (except maybe "change", as if that's automatically a good thing).

The "change" is all BAD and not any good.

these are non-issues if you keep your '/home' and '/' directories on separate partitions
I do a clean install onto my '/' part
then reinstall all my apps using
sudo dpkg --set-selections /home/package.selections && apt-get dselect-upgrade

hence, all my settings are untouched and the issues of where the buttons are located, color schemes,etc. are not an issue - for me at least

if you want a grandma OS then use something else? :)

---

### Post by anechoic on 2010-04-03
> **durand said:**
> That's not the point. It's great being able to customise everything, but that feature is pointless unless people know about it, and the best way to do that is to make it obvious, especially to new users.

being able to customize everything is not a 'feature', it is a core aspect of why most people use Linux 

and if you don't know this about Linux then maybe you should use another OS that is more geared to your level of experience...?
:)

---

### Post by anechoic on 2010-04-03
that being said though, I do agree with you both in that out-of-the-box 10.04 is fugly and carries many dumb design decisions

:)

---

### Post by Slim Odds on 2010-04-03
> **anechoic said:**
> these are non-issues if you keep your '/home' and '/' directories on separate partitions
I do a clean install onto my '/' part
then reinstall all my apps using
sudo dpkg --set-selections /home/package.selections && apt-get dselect-upgrade

hence, all my settings are untouched and the issues of where the buttons are located, color schemes,etc. are not an issue - for me at least

if you want a grandma OS then use something else? :)

So you think that everyone has an existing install of Ubuntu?

There are tons of people learning about Ubuntu for the first time. They shouldn't have to be subjected to these ridiculous defaults.

---

### Post by durand on 2010-04-03
> **anechoic said:**
> being able to customize everything is not a 'feature', it is a core aspect of why most people use Linux 

and if you don't know this about Linux then maybe you should use another OS that is more geared to your level of experience...?
:)

I'm confused about where you thought I was inexperienced with linux. I can easily change the window button placement if I have to (and I did), however, a new user *will not* know how to do that, even a few google searches may not be enough to help. For this reason, you need to have an option in the default ubuntu, mainly because it is what people will be used to so they need to know about the alternatives.

---

### Post by durand on 2010-04-03
> **anechoic said:**
> these are non-issues if you keep your '/home' and '/' directories on separate partitions
I do a clean install onto my '/' part
then reinstall all my apps using
sudo dpkg --set-selections /home/package.selections && apt-get dselect-upgrade

hence, all my settings are untouched and the issues of where the buttons are located, color schemes,etc. are not an issue - for me at least

if you want a grandma OS then use something else? :)

Oh and your button order is still changed whether or not you have a separate home partition. When you update metacity or whatever, the order changes itself.

---

### Post by anechoic on 2010-04-03
> **Slim Odds said:**
> So you think that everyone has an existing install of Ubuntu?

There are tons of people learning about Ubuntu for the first time. They shouldn't have to be subjected to these ridiculous defaults.

when a new user comes to Ubuntu she will have no past version to compare their experience with hence these issues will be of less concern to them 

unless they are coming from XP or W7 (buttons on right) in which case they would have the same experience with the button placement going to OS X (on left)

---

### Post by anechoic on 2010-04-03
> **durand said:**
> Oh and your button order is still changed whether or not you have a separate home partition. When you update metacity or whatever, the order changes itself.

true...easy enough to Google and fix though...
and gconf editor does comes with Ubuntu IIRC

---

### Post by durand on 2010-04-03
> **anechoic said:**
> when a new user comes to Ubuntu she will have no past version to compare their experience with hence these issues will be of less concern to them 

unless they are coming from XP or W7 (buttons on right) in which case they would have the same experience with the button placement going to OS X (on left)

Yeah, they would, but it wouldn't be a nice experience.. Anyway, this conversation is getting pointless [IMG]http://durand1.co.cc/dump/smileys/confused.png[/IMG]

---

### Post by anechoic on 2010-04-03
> **durand said:**
> I'm confused about where you thought I was inexperienced with linux. I can easily change the window button placement if I have to (and I did), however, a new user *will not* know how to do that, even a few google searches may not be enough to help. For this reason, you need to have an option in the default ubuntu, mainly because it is what people will be used to so they need to know about the alternatives.

I wasn't referring to you
I meant the new user who comes to Ubuntu from another OS
Ubuntu is getting dumbed-down enough to be able to reach more people
I just don't want to see this trend continue to the point of absurdity
I mean some of us use Linux because you can tweak and change things
open source and all that
right? :)

---

### Post by anechoic on 2010-04-03
> **durand said:**
> Yeah, they would, but it wouldn't be a nice experience.. Anyway, this conversation is getting pointless [IMG]http://durand1.co.cc/dump/smileys/confused.png[/IMG]

the logic of new users being frustrated with default settings is weak
so I agree it is pointless to continue this discussion
but if you want to get your knickers in a twist about button placement
be my guest! :)

---

### Post by durand on 2010-04-03
> **anechoic said:**
> I wasn't referring to you
I meant the new user who comes to Ubuntu from another OS
Ubuntu is getting dumbed-down enough to be able to reach more people
I just don't want to see this trend continue to the point of absurdity
I mean some of us use Linux because you can tweak and change things
open source and all that
right? :)

Fair point, I don't like it much either. But this is more of a convenience feature, plus it would be very easy to add to System > Preferences > Windows.

---

### Post by anechoic on 2010-04-03
also, check out the new Ubuntu Tweak -- apparently, from what I've heard, they address the button placement issue and made it fairly easy to correct in the new version...

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by billyswong on 2010-04-04
I don't know why this wm buttons change is so sudden and the reasoning behind, but as a novice user what I can say is, **please don't do that.** Just like one won't set the default keyboard as dvorak instead of qwerty, do not copy what Apple did just because those who like Apple like it a lot. Respect our habits please - I am talking about almost everybody who do not use MacOS X here - and revert the old behavior to be default.

For those who use 'things are customizable' as an excuse, customize those buttons to the left by yourselves. Don't force your taste upon us.

---

### Post by kblft on 2010-04-04
I'm sorry if I'm double posting here - but I couldn't find a reference for this anywhere in the post 

If you want the button layout as it is now you need to add also the menu on the corner left

```

gconftool-2 --set “/apps/metacity/general/button_layout” --type string “menu:maximize,minimize,close”

```

---

### Post by lindude on 2010-04-05
Didn't work for me this did though

moving buttons left back to the right

Alt+F2. "gconf-editor" appsmetacitygeneral. Change "button_layout" to:

menu:minimize,maximize,close

And now your buttons are on the right. 
Thanks

---

### Post by neopsalmist on 2010-04-07
Has anyone else had the problem of the buttons being in reverse order on the left, even though metacity listed the string correctly as "close,minimize,maximize:" I edited the string to "maximize,minimize,close" then changed it back to the prior string, and it fixed itself, but I was curious as to whether or not this had happened to anyone else.

---

### Post by everytimeref on 2010-04-07
I must admit that I thought the whole idea of buttons on the left was a rubbish gimmick and I was hell bent on moving the buttons back to where they belong.

Then I tried it and.....

.... I can see the sense of it and think I'll persevere with it.

and remember it's just a button layout in an incredibly customisable interface, it's not worth getting angry over.

Now, can I move the close tab buttons on firefox?

---

### Post by lindude on 2010-04-07
I prefer them on the right, personal choice, it's nice that you can choose. I also didn't like the order they were in, just what I'm use to. Why not move the notification to the left side, (isn't that why they changed the button position?). 
Just as I prefer Google to Bing, I'm glad I could change that back.

---

### Post by robindegen on 2010-04-21
Thank you for posting a fix to this nuisance :)

---

### Post by Potters Son on 2010-04-21
I admit that this post is not to present a unique insight to the discussion, but I feel that it is necessary to demonstrate support for a cause I feel strongly about.

When I booted the Beta 2 CD just now, I was pretty impressed with the UI, but after about the third time that I went to the wrong corner of the window to maximize or close it, I got really annoyed.

PLEASE, Canonical! Put that option to switch the buttons in the Appearance options! I love how customizable Linux is, but you don't do nearly enough with it! Are you afraid that people will get confused by an option in a graphical utility? Switching around the buttons on us will only serve to confuse people even more. You don't have to imitate Apple and strip out features to look "cool". (That's why I didn't buy a mac anyway. They abandoned home/end/page up/down on their laptop keyboards long ago, and I can't live without them.)

---

### Post by Adversus on 2010-05-03
Thank goodness I found this thread. Icons back where they belong, I can stop having spells staring at my screen wondering why my mouse is hovering over empty space where I'm sure there was something before.

---

### Post by ParadoxBlue on 2010-09-18
> **pastalavista said:**
> There is a graphical solution already in the newest [Ubuntu-Tweak]("http://ubuntu-tweak.com/")
Yes but Ubuntu Tweak sucks.

---

