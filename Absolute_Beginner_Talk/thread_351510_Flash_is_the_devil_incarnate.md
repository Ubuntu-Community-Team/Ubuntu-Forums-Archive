---
title: "Flash is the devil incarnate"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Scarlett on 2007-02-02
Ya know... a few months ago when I first started using Ubuntu, everything was great and it worked and it was beautiful... then I tried to install Flash.  I kept banging my head against my desk for at least a month trying to make that darn thing work in a 64 bit system.  I finally found someone's howto on installing Firefox32 and using a beta version of Flash 9 and that was great.  Ok, it randomly crashed a little but it was much better than nothing.

So when I ended up having to wipe everything, due to a total pebcak, and do a fresh install I figured, hey - how hard can it be?  I did it before, I can do it again!  (I really wish I'd posted a bookmark in that thread because now I can't find the thing that worked previously.)

Well whadda ya know, I am once again doing the headdesk over getting Flash to work, only now I've got an entirely different set of problems.  I thought I could Debian-ize an nswrapper with alien and end up with a 32 bit version that worked with amd64.  It seems to have worked for a few other people, anyway.  But what I ended up with is most of the stuff out there on the net telling me I don't have the codecs for mms.  I made a quick trip to automatix where I tried installing various codecs, mplayer and vlc.  

During the install I saw quite a few errors with nswrapper somewhere in there.  It went by so fast I couldn't see what it was saying but in the end I had all these fatal errors on everything I tried to install.  There were also quite a few seg faults and core dumps.  I don't know what that means but it doesn't sound good.   

I'm not really asking for help, since I don't even know what I did to my system... (but if someone just happens to have some telepathic insight into how to reverse this mess, I'd be grateful)... I just wanted to say that I really hate Flash and Adobe's horrible release cycle when it comes to their Linux support (or lack thereof).  </rant>

---

### Post by nitebum on 2007-02-02
I'm totally feeling your pain right now.  In fact I found this thread while looking for a fix. 

There is a petition online, it has about 1000 hits. 
[http://www.petitiononline.com/lin64swf/](http://www.petitiononline.com/lin64swf/)


I wish I could say that its the web designers fault for using flash. But it works for most, and seems to be the most efficient way to host video.

---

### Post by r4ik on 2007-02-02
Maybe this link is any use ?

[http://www.ubuntuforums.org/showthread.php?p=1174435](http://www.ubuntuforums.org/showthread.php?p=1174435)

Good luck !

---

### Post by Scarlett on 2007-02-02
I signed it, but that's Macromedia, as in Shockwave.  While there are a few online Shockwave games I used to play, I can't really say that I miss them now that they're gone.  The really weird thing is, youtube works for me and I know they use Flash.  However, that's just about the only thing that works.  And that's not enough.

I wish you the best of luck getting your Flash to work.

---

### Post by Sef on 2007-02-02
For 64-bit, you could try [Gnash]("http://www.gnu.org/software/gnash/").  It is an open source version of flash.   Warning:  It's currently in the second alpha release, so expect it to be buggy.   It supports version 7 Flash.

---

### Post by Scarlett on 2007-02-02
@r4ik - Thanks, but that's the second one I tried.  By then I'd done at least half the steps in the process so I wasn't sure if the errors I was getting were due to conflicts with what I'd done previously or if it was the same error repeating itself.  From what I can tell, the end result is that the libflashplayer.so should be in /usr/local/firefox32/plugins, which it is, but it doesn't work.

The first one I was using was this:
[http://www.ubuntuforums.org/showthread.php?t=341727](http://www.ubuntuforums.org/showthread.php?t=341727)
And everything worked right up until the last step and somehow I don't have an npwrapper.libflashplayer.so anywhere.

@Sef - Unfortunately, I kinda really need 9.  Don't suppose you know of any support for that, do you?

---

### Post by nitebum on 2007-02-02
this:
[http://www.ubuntuforums.org/showthread.php?t=341727](http://www.ubuntuforums.org/showthread.php?t=341727)

worked for me. For now anyway......[-o<

I did the first method, 
> 
# Alternative n.1: using repository kindly offered by Janvitus:
add the respository and update the sources list: [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)
installation:
Code:

sudo apt-get install nspluginwrapper gsfonts-x11

# end of Alternative 1 


---

### Post by Sef on 2007-02-02
> @Sef - Unfortunately, I kinda really need 9. Don't suppose you know of any support for that, do you?

Unfortunately i don't.   If I do find anything, I will let you know.

---

