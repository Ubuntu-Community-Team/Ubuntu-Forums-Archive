---
title: "OS=Linux Lite-1.0.4 - Surround sound problems."
date: 2013-02-25
forum: Any Other OS
---

### Post by patriot56 on 2013-02-25
Greetings forum.

As the title alludes to, I am using Linux Lite 1.0.4 and I am having problems getting the sound to work properly.

My sound card is a PCI - "**Creative Labs, Sound Blaster Live 5.1" surround sound card,** and the problem is, I cannot get sound from anything other than the front speakers.

I have tried adjusting the options in the sound preferences - Menu> Multimedia> Audio Mixer (and) PulseAudio Volume Control and I have also opened the **Terminal** and, using the alsamixer command, I have confirmed the settings for the sound card.
Still, no sound in the rear speakers.

At this point, I am all out of ideas - most likely due to my limited skill set - so if anyone has any suggestions, I am humbly open to suggestions. O:) 

Thank you in advance.

Respectfully,

P56

---

### Post by codemaniac on 2013-02-25
Moved to "**Other OS/Distro Talk**".

---

### Post by patriot56 on 2013-03-06
I finally found a solution to this issue.
It seems that getting full, and* true*, 5.1 surround sound working on Linux is not as easy as you might imagine. See [here]("http://www.halfgaar.net/surround-sound-in-linux").

In an attempt to help anyone reading this post with the same problem,  I am posting the solution that I used.

It worked well for me and it is my hope that it will help anyone else with the same problem.

Though the information listed on **[COLOR=#0000ff]halfgaar's site [/COLOR]**(*listed above*), is articulate and (I can only assume) technically accurate, it does require a certain level of knowledge and/or familiarity with computer sound systems, ie., sound cards, sound applications, etc., that I do not have. Parts of his article did help however, but for the most part, -at least in my case- it created more confusion than anything else.

I don't know about you, but I don't have much knowledge in the area of the inner-workings of multimedia (I wish I did) so, I had to look for a solution that was easier to understand, (at least for me).  :wink:

This is what I came up with:
 
[LIST]
[*]First, open a Terminal and enter the command ```
alsamixer
``` 
[*]Press F6 and make sure your soundcard is selected as the default device.  Next, open your music player and start a song.
Across the bottom of the [FONT=courier new]alsamixer[/FONT] display, you should have a lot of channels.  While the music is  playing, scroll along the bottom (using the right/left arrow keys) and make sure none of the channels show 'MM'.  If any of them do, toggle them to '00' using the '**M**' key.  You may have to scroll across the entire display to the right to ensure you have checked every single channel. 
[/LIST]
 
If you are still not getting full surround sound from your speakers, try this:


[LIST]
[*]Open a Terminal, *if it is not already open,* and enter: ```
sudo gedit /etc/pulse/daemon.conf
``` obviously, this assumes that you have gedit installed. 
[/LIST]
 
Near the bottom of the file, you should find a line which looks something like this:
**[FONT=courier new];default-sample-channels = 2[/FONT]**

The semi-colon is a comment, so this line isn’t actually doing anything unless you remove the proceeding ;.  It would be a good idea to leave this line alone and add a new line at the bottom of that section.  Like this: 
**default-sample-channels = 6**

If you’re using a 5.1 system, the number of channels will be 6.  If 7.1 then you will want to change the number to 8. 



[LIST]
[*]Save and close the file. 
[*]Reboot so that your changes will take effect.  After you return from the reboot, you will need to go into your "Sound Preferences" menu and select the **[COLOR=#0000cd]Hardware[/COLOR]** tab. This can be accomplished in a couple of ways. 
[/LIST]
  
[LIST=1]
[*]Right click on the sound (speaker)     icon in your control panel at the bottom of your screen and select preferences or, 
[*]Goto, System > Preference > Sounds from the main menu and click on the Up/Down arrows to select your hardware profile. 
[/LIST]
 You can try several of the options displayed If you aren't sure about your particular configuration.

Depending on your distribution, there should be a drop down box next to "**[COLOR=#0000cd]Profile[/COLOR]****" **which says “**[COLOR=#008000]Test Speakers[/COLOR]**”. Because the Linux distribution that I use didn't have these options, I installed**[COLOR=#4682b4] GNOME ALSA Mixer[/COLOR]**, an application that provided similar options. Still, it didn't have the option to "Test Speakers" but I didn't need to test my speakers because after installing GAM and making the appropriate settings, I now had 5.1 surround sound.
However, if you do not have the option in your profile to *Test Speakers* you can use this [link]("http://www.youtube.com/watch?v=w0eaV8r-nXQ") to conduct a speaker test.

If these instructions appear to be disjointed, or cause more questions than answers, I apologize.
This is the first post of this kind for me, and I am still learning myself.

If you have any questions, comments or concerns, please feel free to PM me.
  
 I wish to give credit where credit is due.
I have tried to paraphrase these instructions to the best of my ability however, **most everything in this post came from one or more of the following sources**:
[[COLOR=#0000ff]http://www.halfgaar.net/surround-sound-in-linux[/COLOR]]("http://www.halfgaar.net/surround-sound-in-linux")
[URL="http://alexsleat.co.uk/2011/12/03/setting-up-surround-sound-in-linux/"]**[COLOR=#0000ff]http://alexsleat.co.uk/2011/12/03/setting-up-surround-sound-in-linux/[/COLOR]**
[/URL]**[[COLOR=#0000ff]http://linux.die.net/man/1/alsamixer[/COLOR]]("http://linux.die.net/man/1/alsamixer")**[COLOR=#0000ff]
[/COLOR]
I sincerely hope that this will prove to be helpful to someone else that might be struggling with this problem.  
 


 Cheers
 Patriot56

---

