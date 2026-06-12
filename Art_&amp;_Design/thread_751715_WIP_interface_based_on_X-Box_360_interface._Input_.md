---
title: "WIP interface based on X-Box 360 interface. Input appreciated."
date: 2008-04-10
forum: Art &amp; Design
---

### Post by st0n3cutt3r on 2008-04-10
I've always thought that the interface for the XBox 360 was very intuitive and easy to work with.

For anyone who is unfamiliar with it, the system's home menu is a tabbed screen (see attached image). 
They have the benefit of not actually having a whole lot of options they need to offer (it's a video game console/media center...  you don't really need much), but I think that it would be fun to try to integrate into a desktop environment.

When you hit the home button on the controller (the equivalent of a 'super' key) it opens a tab from the left side with various menu options, I *believe* the content of the menu is context sensitive, but I'm not certain.

I've not spent a terribly long time developing a mock-up for it yet, as I'm still trying to figure out how it should all work, but pretend for the sake of this that there is a 'super' key that isn't tied to anything else, and could easily be pressed on a keyboard to pull up a menu.

What things should appear on this menu?  how would you make it more accessible (and FASTER) than the current system?

A preliminary mock-up is attached of what you might get for a default menu from the desktop, giving you access to important and (sometimes) frequently needed settings.

The idea is to put as much as possible on one menu system so that you can take as much off of the toolbars, and other menus. Basically reorganizing what we already have for toolbars and menus into a more logical, importance-organized, simple, intuitive system.

From bottom to top on my mock-up (screenshot.png) I've got a quit button so that it can come off of the toolbar. I figured it's out of the way where it is in the mock-up, and is still easy enough to access.

Then I have a button to access administration settings - Too many settings to be dropped in a menu like this, but it could just open an administration settings window (equivalent to the control panel in windows).

Then general preferences that change on a regular basis in an in-line (tabbed) menu.
I figured Volume settings should go here, as well as display settings, network settings, and I couldn't think of anything else, but I'm sure that somebody can.

for volume, you can see what I expected to be there in the preview:  a volume slider, and a mute button, then below a microphone slider and mute button for that.  Then below, a check box for enabling/disabling the equalizer, and the sliders for *it* (grayed out when disabled).  Then some buttons to pull up other, less frequently changed settings (general sounds settings and speaker settings).  
I've already realized that there should probably be a quick drop-down to save/choose predefined configurations for the equalizer, but I didn't include that, and there should be a { **?** }  help button in the top right corner of each sub-tab (volume, display, network) which would open up a help window with information about how to use, and what the tools were in that tab.  (most people I know don't know what an equalizer is, nor how to use it).

On the display tab, from top to bottom, I think there should be a brightness slider, maybe a button for engaging the on-screen keyboard, another for the on-screen magnifier? perhaps a small in-line scrollable list for changing wallpaper or theme?  I haven't really thought this one through fully yet, but again, that's what this thread is for.

On the network tab, there should be an in-line list for wireless networks if the computer is using wireless to access the Internet/network(to easily select a network), or maybe just display what network the computer is accessing if it's wired.  you could also show network usage in a simple bar graph for up/down speeds, and the (k)b/s being used.  Also an in-line menu for network folders would be nice, and then links to the network interface options and other relevant configuration dialogues.

Above that, a search box would be nice to search your computer.  type what you want in the box, hit enter, and a window would pop up with your results. (and the tab would disappear)

At the top, the user picture/name could be displayed, as well as the account type, a digital clock, the date....   and just below that a link to the home folder?

Also, clicking the user picture/name could take you to a window with your picture settings, maybe also password settings?....   

Alright, that's what I've got for now.
Looking at the image of the xbox menu makes me think that it could be nice to be able to browse your home folder like that, having tabs for pictures, movies, music, etc. (any folders that the user has in their home folder.  possibly a default tab with the non-folder contents of their home folder displayed, and then double-clicking a folder on any given tab would simply take you down a level w/in that branch, and show the contents of the folder you selected.  I think you can figure it out....  :)

Alright, thoughts and suggestions, please.  Other mock-ups welcome as well (to be integrated into what I already have or to substitute in part)

(don't mind the colors in the mock-up, they're just to help me see/keep track of things)
Thanks!

---

### Post by st0n3cutt3r on 2008-04-10
here is a slightly revised version.  more updates coming as I get more done.

---

### Post by st0n3cutt3r on 2008-04-11
a little more color added and some things slightly shifted.

(really, nobody thinks this is a cool idea, or could be fun to pursue? :( )

---

### Post by gali98 on 2008-04-11
I think its a pretty cool idea. I'm not sure I understand completely what you're doing though.
Anyway cool pics. kinda reminds me of a revamped old mac menu.

---

### Post by gali98 on 2008-04-11
Okay now that I actually read it all :)  I think I kinda understand.
So I got a few questions for you...
First is this code that we are seeing, or just a picture of what you want to do?
Second how does this integrate into Gnome?
I like the idea of the home folder and such...
Kory

---

### Post by st0n3cutt3r on 2008-04-11
it's not code, I just hadn't decided on what to use for sliders yet, and only being this far in developing the mock-up, I didn't want to devote an hour+ to creating reasonably nice looking sliders when it took me all of 3minutes to create what I've got in text.

Basically, I think this would be called to the front (slide quickly in from left) by pressing the super(windows) key.  there'd need to be some tinkering done with how it read the keystroke so as not to interfere with other things that use the super key in their bindings, but something easy to access, easy to remember, and fast.

on the xbox, when you press the super key, it pulls up a menu that is relatively similar to what I've created so far, with various context-sensitive menu options, a few buttons to access your preferences, etc.  By holding down the super key (on the xbox) you get a tab that comes up from the right instead, offering you options for shutting down the console/quitting your activity?  I can't remember exactly, but I didn't think it was as important... at least not to this mock-up.

The goal is to put useful information/settings somewhere useful.  out of the way when you don't need it, but *extremely* fast to access and manipulate when you do. No multiple-level menus to navigate, then additional dialogues to wait for, nor cluttered toolbars.

======================
I see myself realistically tapping the super key twice in quick succession (like literally no more than half a second between hits) to open the menu, glance at the weather/temperature, and close it again.   Also things like brightness on my laptop, I don't change often, but once in a while I want to, and it takes me WAY too long to figure out how to do it through the GUI (I'm typically donating plasma and wanting to extend my battery life when I want to change it, so using the hardware switch can be a bit tricky as I only have one hand to work with on those occasions).  I can come up with more realistic scenarios for using something like this, but I was hoping to have suggestions from other people for what to include.   (thanks, by the way, for the responses!)

---

