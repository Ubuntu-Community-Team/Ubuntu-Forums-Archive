---
title: "Some help setting up Mint 12 please"
date: 2011-11-27
forum: Any Other OS
---

### Post by bigseb on 2011-11-27
I finally got Mint 12 and installed it and now I'm happy. I also very rusty in the ways of Linux so...

... how do I add a nvidia ppa to install latest nvidia drivers via synaptic?

Thanks

PS there'll prolly be more coming later :D

---

### Post by bluexrider on 2011-11-27
did you run the update, ie: about 225 packages?

synaptic has the latest drivers and imho I might not consider putting any proprietary drivers in just yet......Mint 12 is just a newborn, don't break the baby

---

### Post by bigseb on 2011-11-27
> **bluexrider said:**
> did you run the update, ie: about 225 packages?

synaptic has the latest drivers and imho I might not consider putting any proprietary drivers in just yet......Mint 12 is just a newborn, don't break the baby

Update? How? I just opened synaptic and pressed reload... have I missed something? Also, the limited bandwidth thing, do I really need all updates? Anyway I'm the little 'Install Drivers' thing at the top right, lets hope that'll do it for now.

By the way, you've been a huge help in my other threads. Much appreciated.

---

### Post by aeronutt on 2011-11-27
By default in Mint 12, update manager is running, and in gnome-shell, is the little shield in the top menu. If it's not there, go to the shell, and type 'update', and you'll see the update manager, and start that. I'd at least update all level 1 and 2 packages.

---

### Post by bluexrider on 2011-11-27
Go to the terminal:

sudo apt-get update && sudo apt-get upgrade

You may be left with 3 packages not installed which would be the new kernel, ignore that for now.

Set back and wait. Its going to take a while

---

### Post by bigseb on 2011-11-27
> **aeronutt said:**
> By default in Mint 12, update manager is running, and in gnome-shell, is the little shield in the top menu. If it's not there, go to the shell, and type 'update', and you'll see the update manager, and start that. I'd at least update all level 1 and 2 packages.


I don't know what you mean by shell... :(

---

### Post by aeronutt on 2011-11-27
Sorry, shell is probably the wrong word. Either hit the 'windows' button or move your cursor to the top left corner. Then type in 'update manager'. Or, do what bluexrider posted. :)

---

### Post by bigseb on 2011-11-27
> **bluexrider said:**
> Go to the terminal:

sudo apt-get update && sudo apt-get upgrade

You may be left with 3 packages not installed which would be the new kernel, ignore that for now.

Set back and wait. Its going to take a while

Okay I found the update thingie but there's a bigger problem...

I pressed the 'install drivers' button on the right hand side of the top bar. The download started but then my connection was dropped about a third of the way through. I tried to cancel the update but that caused jockey-gtk (?) to freeze so I kill it in the terminal. I wanted to restart the 'install drivers' but it wouldn't respond so I restarted the PC. Now the graphics are completely rubbish at 1024 x 768 (should 1920 x 1080). The monitor preferences would go higher than 1024 x 768. I logged out and tried the other options (gnome, gnome classic, etc) but they were all the same.

People say the best way to learn linux is to break it, then fix it. How? Haven't a clue where to start... :(

---

### Post by bigseb on 2011-11-27
> **aeronutt said:**
> Sorry, shell is probably the wrong word. Either hit the 'windows' button or move your cursor to the top left corner. Then type in 'update manager'. Or, do what bluexrider posted. :)

Now there is nothing in my top left corner (read my previous post)

---

### Post by bigseb on 2011-11-27
Nevermind, I redownloaded the driver, all sorted.

Side question, does mint have the wobbly windows like Ubuntu?

---

### Post by bluexrider on 2011-11-27
I lower my head in sorrow. You broke the baby. IMO it would be easier to do a reinstall than try to fix it. 

Get a stable running system before trying to install additional drivers.

NOW! back to the drawing board.....

---

### Post by bluexrider on 2011-11-27
> **bigseb said:**
> Nevermind, I redownloaded the driver, all sorted.

Side question, does mint have the wobbly windows like Ubuntu?

its a compiz thing you have to download 
comipz-fusion-plugins-extra and comipz-plugins-extra 

then enable the plugin.

However, be warned Caja is your desktop manager NO nautilus anymore

---

### Post by bluexrider on 2011-11-27
BTW thought you might want to see this [http://forums.linuxmint.com/viewtopic.php?f=42&t=86813](http://forums.linuxmint.com/viewtopic.php?f=42&t=86813)

---

### Post by bigseb on 2011-11-28
> **bluexrider said:**
> its a compiz thing you have to download 
comipz-fusion-plugins-extra and comipz-plugins-extra 

then enable the plugin.

However, **be warned Caja is your desktop manager NO nautilus anymore**

I don't understand the relevance of this. Does compiz only work with nautilus?

---

### Post by ernestj on 2011-11-28
> **bluexrider said:**
> BTW thought you might want to see this [http://forums.linuxmint.com/viewtopic.php?f=42&t=86813](http://forums.linuxmint.com/viewtopic.php?f=42&t=86813)

Are you kidding me? This scares me, I can not imagine if I was a complete newbie and having, needing or wanting to do all of this; just to get the system working to an acceptable position. That is like trying to turn a Honda into a Porsche. 

I will stick with Xubuntu. I did some tweaking, but not to this level.

---

### Post by bigseb on 2011-11-29
> **ernestj said:**
> Are you kidding me? This scares me, I can not imagine if I was a complete newbie and having, needing or wanting to do all of this; just to get the system working to an acceptable position. That is like trying to turn a Honda into a Porsche. 

I will stick with Xubuntu. I did some tweaking, but not to this level.

I thoguht it was a bit much too. More importantly I don't understamd what the purpose of all of it is.

---

### Post by shuttleworthwannabe on 2011-11-29
I think give Ubuntu and Mint a few more iterations (like 12.04 plus 2), and I am sure the devs will tweak the OS to match the noobie's requirements. All this tweaking is because of the move to Gnome 3.x/with Shell.
For now imagine you are starting Ubuntu/Mint like we were in 2004+

---

### Post by aeronutt on 2011-11-29
> **ernestj said:**
> Are you kidding me? This scares me, I can not imagine if I was a complete newbie and having, needing or wanting to do all of this; just to get the system working to an acceptable position. That is like trying to turn a Honda into a Porsche. 

I will stick with Xubuntu. I did some tweaking, but not to this level.

None of those tweaks are necessary to use the OS at an acceptable level.

---

### Post by ernestj on 2011-11-30
Maybe I was a bit harsh. I have been having problems coming to grips with GNOME 3. There are parts that I love, like the way the icons are presented when you click applications. I like the way all of the open windows are displayed when you click the infinity symbol. I think those need to rearranged to be more livable. Like in Unity, when you have several windows open for one application and you click the icon in the launcher and it shows all of those windows. I went with Xubuntu cause I wanted to install AWN dock. Xubuntu is customizable, LIGHT, fast and AWN works really well with it. Originally, I downloaded 12RC ISO and was hoping to do the same set-up. I could not bring myself to do it. GNOME 3 still needs to grow and mature to become acceptable IMO. I wanted to start using it because I feel that it will be the standard in and widely accepted in the future. I DO feel that UNITY is light-years ahead of GNOME 3. I do like UNITY a lot. 
The problem now is that I absolutely Love Xubuntu and probably will not disto hop for a while. I an anxiously awaiting LUNA though.

---

