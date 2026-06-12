---
title: "Compiz &amp; Xgl have made everything too slow!"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Redptc on 2008-02-16
I have had to resort to Windows to make this request, Xgl has slowed things down too much. I may need more ram, perhaps!

How can I shut xgl, compiz down? Temporarily so that I can bring thing back  again as needed.

One forum thread indicated that the following would disable......

[COLOR="DarkRed"]metacity -- replace[/COLOR]     

 Do i just type that into a terminal?     :confused:

---

### Post by luvinit on 2008-02-16
Yes, type it in the terminal.

---

### Post by Redptc on 2008-02-16
Thanks for the help but things are still running slow. It appears to me that all this Xgl still operates.

Perhaps you can advise how to create a file named     ~/,config/xserver-xgl/disable

---

### Post by rainwalker on 2008-02-16
I used to have a script that would switch between Compiz and Metacity when I used it, let me see if I can find it for you...

---

### Post by Redptc on 2008-02-16
I'd appreciate your help, Rainwalker, can you tell me how to 'create a file'?

I have a switch called [COLOR="Navy"]compiz-switch[/COLOR] which turns compiz off/on!

---

### Post by rainwalker on 2008-02-16
What do you mean? 
Are you saying you already have the script to switch it, but you need a way to use it?

---

### Post by Redptc on 2008-02-16
> **rainwalker said:**
> What do you mean? 
Are you saying you already have the script to switch it, but you need a way to use it?

I have a switch for compiz that turns it off/on but the xgl server seems to continue to operate and slow thiings down as a result.

Somewhere in this forum, it advised to disable Xgl by the script....metacity --replace

I did that which seem to be succesful in the terminal but has no apparent effect.

However, when I installed the xgl server, a pop-up indicated that it would install automatically at login. That was when things got very slow. At the same time, it advised,'To disable Xgl autostart create a file named *~/.config/xserver-xgl/disable*' Essentially, I can't (don't know how) to create that file! Can you help?

---

### Post by corney91 on 2008-02-16
I've been having severe slowness of Compiz/XGL as well. I just use Metacity now by going into gconf-editor and navigating to /desktop/gnome/applications/window_manager and setting both current and default to /usr/bin/metacity. This makes Metacity start on login.
Of course this doesn't solve your problem if you want the effects...

---

### Post by Redptc on 2008-02-16
> **corney91 said:**
> I've been having severe slowness of Compiz/XGL as well. I just use Metacity now by going into gconf-editor and navigating to /desktop/gnome/applications/window_manager and setting both current and default to /usr/bin/metacity. This makes Metacity start on login.
Of course this doesn't solve your problem if you want the effects...

Gee, I wish I had never heard of the 'effects'! I read that it was possible to have transparency which sounded quite impressive. Thought i would give it a try and now I am thinking I should have just left it all in the can!

Thanks for your tip! Do you know how to 'make a file' in the terminal?

---

### Post by icechen1 on 2008-02-16
Xgl slow me down too,because it is still experimental.Try to use AIGLX when possible  or use metacity like your command.

---

### Post by jordanmthomas on 2008-02-16
To make a file in your terminal.
```
cd    #make sure you're in your home directory
mkidr .config     #make a folder in case it's not there
mkdir .config/xserver-xgl     #make a folder in case it's not there
touch ~/.config/xserver-xgl/disable   #make the file

```

---

### Post by doorknob60 on 2008-02-16
```
 nano ~/.config/xserver-xgl/disable
```
And just type a letter and backspace (so it says you modified it) and press ctrl-X and say yes when it asks to save :)

Aww jordan beat me, but his way might be better anyways :P

---

### Post by jordanmthomas on 2008-02-16
Yours is simpler; simpler is better.  :)

---

### Post by xeth_delta on 2008-02-16
> **icechen1 said:**
> Xgl slow me down too,because it is still experimental.Try to use AIGLX when possible  or use metacity like your command.

I agree. To the OP, try using the regular x.org X11 server together with AIGLX if you want to run compiz. Was there any specific reason why you needed xgl?

---

### Post by Redptc on 2008-02-16
> **icechen1 said:**
> Xgl slow me down too,because it is still experimental.Try to use AIGLX when possible  or use metacity like your command.

Thanks mate, do you know how to make a file in a terminal? I would like to create a file called ~/.config/xserver-xgl/disable

I have very little know-how regarding this terminal business and I just can't find out how to make a file.

---

### Post by jordanmthomas on 2008-02-16
You can also make the file in nautilus (your file browser)
1.  Open up your home directory.
2.  Press ctrl - h to show hidden files (ones that start with . )
2.  Find the folder .config
3.  If it doesn't exist, right click and go to "create folder" to make one
4.  Enter the .config directory.
5.  Look for the xserver-xgl directory.
6.  If it doesn't exist, create it.
7.  Enter the xserver-xgl directory.
8.  Right-click and go to Create new file and name it disable.

Log out / back in and xgl *should* be disabled.

(do you see why people give terminal instructions instead of GUI ones?  4 steps vs. 9, and the terminal could really be cut down to 1 or 2)
```
mkdir -p ~/.config/xserver-xgl && touch ~/.config/xserver-xgl/disable
```
one line.  :)

---

### Post by Redptc on 2008-02-16
> **xeth_delta said:**
> I agree. To the OP, try using the regular x.org X11 server together with AIGLX if you want to run compiz. Was there any specific reason why you needed xgl?

No, basically it was some forum suggestion to get things up and running! I followed the recommendation and ended up with a bit of a headache. Not comletely solved yet and I may see how things go with your suggestions.

Thanks for your help.

---

### Post by forrestcupp on 2008-02-16
I assume you were using Xgl because you have an ATI video card.  The honest truth is that these cards suck for Compiz no matter how you do it.  We keep hoping with each driver release that they will have the kinks worked out.

If I were you, I would just turn off your effects and uninstall Xgl.  There is no point having it if you can't functionally use it.  Go to System->Preferences->Appearance and in the Visual Effects tab, turn it off.  Then get in Synaptic and search for Xgl and uninstall it.  Then when you restart your computer, you should be ok.

If you want to run effects, do it right and search for threads on how to use fglrx with aiglx instead of Xgl.  You'll have to use the newer ATI drivers from their web site, and [Envy](http://albertomilone.com/nvidia_scripts1.html) is an easy way to install them.  But I'll warn you, Compiz is slow as molasses even doing it this way.  There is presently no good choice with an ATI card.

---

### Post by Redptc on 2008-02-16
Great stuff, Jordan, that's perfect!

---

### Post by Redptc on 2008-02-16
> **forrestcupp said:**
> I assume you were using Xgl because you have an ATI video card.  The honest truth is that these cards suck for Compiz no matter how you do it.  We keep hoping with each driver release that they will have the kinks worked out.

If I were you, I would just turn off your effects and uninstall Xgl.  There is no point having it if you can't functionally use it.  Go to System->Preferences->Appearance and in the Visual Effects tab, turn it off.  Then get in Synaptic and search for Xgl and uninstall it.  Then when you restart your computer, you should be ok.

If you want to run effects, do it right and search for threads on how to use fglrx with aiglx instead of Xgl.  You'll have to use the newer ATI drivers from their web site, and [Envy](http://albertomilone.com/nvidia_scripts1.html) is an easy way to install them.  But I'll warn you, Compiz is slow as molasses even doing it this way.  There is presently no good choice with an ATI card.

Where were you when I started all this business, that's where I want to be, at the point where I don't have any effects...and no Xgl!

Thanks mate!

---

### Post by xeth_delta on 2008-02-16
> **forrestcupp said:**
> I assume you were using Xgl because you have an ATI video card.  The honest truth is that these cards suck for Compiz no matter how you do it.  We keep hoping with each driver release that they will have the kinks worked out.

If I were you, I would just turn off your effects and uninstall Xgl.  There is no point having it if you can't functionally use it.  Go to System->Preferences->Appearance and in the Visual Effects tab, turn it off.  Then get in Synaptic and search for Xgl and uninstall it.  Then when you restart your computer, you should be ok.

If you want to run effects, do it right and search for threads on how to use fglrx with aiglx instead of Xgl.  You'll have to use the newer ATI drivers from their web site, and [Envy](http://albertomilone.com/nvidia_scripts1.html) is an easy way to install them.  But I'll warn you, Compiz is slow as molasses even doing it this way.  There is presently no good choice with an ATI card.

I completely agree with you that the best way to go in this case would be to uninstall xgl and use AIGLX, but would like to add that I have managed to run beryl (fork from compiz and partly predecessor to the current compiz fusion) at a quite acceptable speed on an old laptop of mine which has an ati card. The card is a radeon mobility 9000 IGP, at 1024x768. I used the open source driver provided by x.org.

Redptc, what card model do you have?

---

### Post by Redptc on 2008-02-16
Thanks everybody, I have gone 'back to basics' and me and my machine are much happier!

I followed forestcupp's very frank suggestion.

Appreciate you consideration xeth_delta but I think I will 'study' things abit more carefully and go from there.

For the moment, I'm passing on 'effects'. Thanks All!

---

### Post by Redptc on 2008-02-17
Xserver just won't give up! Now that I think I have uninstalled it, a pop-up window arrives each time I boot to tell me that xserver thinks my keyboard is different that in Gnome's record???? and what would I like to choose. All this, even though it has been 'completely' uninstalled!

I can't get rid of it! I have to choose one or the other every feckin time I boot. It doesn't matter which one I choose everything runs fine but I have to choose. Anybody know how to get rid of this nuisance?:roll:

---

### Post by Redptc on 2008-02-17
Just too hard??

---

### Post by Caligula on 2008-02-17
there's a box there you can tick that'll save whatever you choose.

That should solve your problem.

---

### Post by Redptc on 2008-02-17
> **Caligula said:**
> there's a box there you can tick that'll save whatever you choose.

That should solve your problem.

Oh, don't I wish! I can't find a box other than that which allows you to manipulate the window itself. The only choice I get is Xgl or Gnome.

Have you experienced a similar thing?

---

