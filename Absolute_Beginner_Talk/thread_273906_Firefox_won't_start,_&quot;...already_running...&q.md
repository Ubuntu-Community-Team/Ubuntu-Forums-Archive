---
title: "Firefox won't start, &quot;...already running...&quot;"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by mjpatey on 2006-10-09
<edit> I resolved this issue.  If you're interested, see my post near the top of page 2! </edit>

When I try to start Firefox or Swiftfox, I get the following error message:

> Firefox is already running, but is not responding.  To open a new window, you must first close the existing Firefox process, or restart the system.

So I check Processes, and nothing called Firefox (or Mozilla or Swiftfox) is running, so I'm not sure what needs to be terminated.  A reboot does get rid of the rogue process, but once Firefox is opened and closed again, I get the same result when trying to re-launch it.

So I uninstalled Firefox and Swiftfox.  Re-installed Firefox only, but the problem continues!

I did not do a "complete removal" in Synaptic, just a "removal".  Will a complete removal followed by an install fix this, or is that asking for trouble?

Also, another strange symptom in Firefox that's been happening at the same time is that I can fill in text fields, but not "enter" the text.  It displays in the text field, but clicking the associated "enter" button (or hitting Enter on the keyboard) doesn't send the text to the website.

Weird stuff... anybody have any ideas?

Thanks!

-Mark

---

### Post by foxmulder881 on 2006-10-09
Do a complete removal of Firefox and then reinstall. That should clear up any issues.

---

### Post by mjpatey on 2006-10-09
Well, I tried a complete removal and reinstalled.  Both problems are still present!

1.  Once Firefox has been closed, it can't be opened again because something thinks it's still running somewhere...

2.  I can't enter any text into text fields in Firefox when it does run (which is only the first run after a reboot!)

Anyone?  Thanks for any help you may have!

-Mark

---

### Post by TheWizzard on 2006-10-09
```

killall firefox
```

this should do the trick.

remove & re-install are typical windows-reflexes. often not usefull in linux, only if you're sure you have dependency problems. rather than remove & re-install you can try removing the configuration folder (~/.mozilla/firefox).

---

### Post by DirtDawg on 2006-10-09
try ```
 killall firefox-bin 
```
I'm not sure about the text field business. Maybe once you kill the process at the roots it will "fix" itself.

---

### Post by HereInOz on 2006-10-09
Try opening a terminal and starting firefox from the terminal.  Just type firefox at the prompt.  It may give you an error message that will give you a clue as to what is happening.

It also may be a total waste of time, but it is always worth a go as you often see what is happening in the background, whereas opening from the desktop is not very enlightening.

---

### Post by mjpatey on 2006-10-09
Very weird.  I tried "killall firefox" and "killall firefox-bin" and both reported "no process killed".  Then when I tried opening Firefox from a Terminal, I got the same error message I described in the original post ("...already running...").

This is really perlexing.  If I were in Windows right now, I'd check for viruses and spyware!

Oh, just saw the end of Wizzard's post... I'll try removing the config folder and post back.

-Mark

---

### Post by xpod on 2006-10-09
If it does not compute............you must reboot;) 
Thats my failsafe option when nothing else works.
I used to have similar issus with synaptic when no other program
managers were open.

---

### Post by Psquared on 2006-10-09
Have the same problem occasionally with Firefox. It started after a FF upgrade so I think there's a bug in 1.5.0.7. I'm thinking of getting rid of FF and SF and installing IceWeasel anyway so maybe that will take care of the problem.

---

### Post by bulldog on 2006-10-09
What kind of extensions have you installed?

Maybe is one of them responsable for this misbehavior, specially after an upgrade it's possible that one of them need to be upgraded too.

I myself have firefox 1.5.0.7 and ditto swiftfox and no problems.

---

### Post by doobit on 2006-10-09
I had a similar problem with FireFox, so I got a new mouse and the problem went away. The left mouse button does a little bit of a double bounce sometimes. Firefox closes the second instance almost immediately, but the GUI responds a little more slowly leaving the dialog that says that two instances are open, but one is not responding. Just close the dialog. You could also reduce your mouse sensitivity, but I had to get a new mouse.

---

### Post by mjpatey on 2006-10-09
Fixed it!  Here's what I did...

Since I'm dual-booting with Windows, I keep my profile folder ("xxxxxxx.default") on a shared FAT partition and point both Firefoxes (Ubuntu and Windows) to it so I have the same bookmarks, extensions, etc., in both OSes.

On a hunch, I booted into Windows for the first time in about a month (yay!), and immediately, Google Desktop reported a corrupt file in my Firefox profile folder on the shared partition!  The file was called "cookies.txt.moztmp" and I assume was auto-generated by Firefox and subsequently corrupted during a crash or "unexpected shutdown" (I do have a toddler).

The file was dated 2 days ago, when my problem first started occurring.  This looked promising!  I moved it to the Windows recycle bin, rebooted into Ubuntu.  Voila!  I'm now back to a healthy Firefox, with full text-field typing ability, and can close and reopen it without fear of a nonexistent unkillable process getting in the way.

I guess Windows is good for something after all!  Actually, it was Google Desktop that reported the problem during its scanning process.

Thanks for all the help, folks!

---

### Post by Psquared on 2006-10-09
> **bulldog said:**
> What kind of extensions have you installed?

Maybe is one of them responsable for this misbehavior, specially after an upgrade it's possible that one of them need to be upgraded too.

I myself have firefox 1.5.0.7 and ditto swiftfox and no problems.

my problem just kinda went away on its own .... just the way it appeared.

strange, very strange ..... (i did update a couple of extensions and deleted a few i was not using so you may be right - it might be a faulty or poorly designed extension - I read the ratings on extensions now!!!!)

---

### Post by TheWizzard on 2006-10-10
@ mjpatey

good to hear your problems are solved. :D 
there are some issues regarding problem-solving i want to share. 

1) approach your problem top-down with logical steps. 
a) create an additional user, named "test". you can use this user account to find out if the problem is local or global. 
b) start the application from the command-line. this normally gives all the feedback needed to solve problems with applications. 
c) check the log-files. 

2) complete removal and then reinstall is not the way to solve stuff in linux. neither is reboot (only if you need to reload the kernel). these are the windows ways of solving problems: trial and error. 

3) report non-standard configurations if you post a question! 
> I'll try removing the config folder and post back.

this doesn't solve your problem because you changed the location of your profile folder. people cannot give good advice if you don't give the required information. BTW, i would advice you not to share your complete profile folder because this may cause future problems. just share your bookmarks file. 

4) backup not only the /home folder, but also the /etc folder. 

> I guess Windows is good for something after all! Actually, it was Google Desktop that reported the problem during its scanning process.
nope. windows is good for gaming, nothing else! 
you just need to get familiar with another way of approaching problems. the linux way of solving problems is different, so it takes some time to get used to this.

---

### Post by kalle314 on 2006-10-10
Probably this would have been resolved by simply rebooting ubuntu, but I agree with TheWizzard that this isn't a good way to solve the issue.
If you don't have the time to try to find the bug in Firefox or whatever is causing this, you might try to find the process with "ps -ef | grep firefox", which I did when I had a similar firefox problem recently - looking at the processes with the "top" command (if that is what you did) will probably not show the firefox process if it is a "zombie".

---

### Post by mjpatey on 2006-10-10
@ kalle314-

No, reboots didn't fix it (pretty sure I stated that somewhere, but just in case I didn't, here it is!)

@ TheWizzard-

I appreciate the advice.

And believe me, had it occurred to me at the time that my non-standard configuration could be an issue (Profile folder located on a different partition), I would have reported it.  But I don't think the location of the profile folder had any effect on the problem; it's just like having it in the standard location, as long as the main config file (I forget its name, maybe profile.ini?) points to it properly, and it did.  I'm pretty sure that "cookies.txt.moztmp" file would have kersploded my profile no matter where the profile folder lived.  It happened under Ubuntu, not as a result of booting into Windows (since I hadn't done that in about a month), so the problem was definitely not caused by the folder being shared with Windows.

I like the "test" user idea.  I can see how that would be very useful in a lot of cases.  As soon as I have time to figure out how to do it, I'll make one.  In this case, an additional user profile in Firefox would have helped solve the problem, so I'll make one of those, too.

Please understand that my positive comment about Windows (or Google Desktop, as it turns out) was not meant to indicate that I prefer it to Ubuntu.  I'm just pleasantly surprised to have discovered and fixed my problem through unexpected means using a tool it would never have occurred to me to use.

> 
Quote:
I'll try removing the config folder and post back.

this doesn't solve your problem because you changed the location of your profile folder. people cannot give good advice if you don't give the required information.

First off, it did solve the problem... I just wanted to keep my bookmarks and other settings, so I pressed on trying to get the problem fixed in my existing profile.  I can see you really don't like the way I've gone about this.  But removing *did* help solve the problem, and the folder's location had no effect on anything... when I removed the Profile folder, FF was forced to re-create its profile files and essentially create a new empty profile, which didn't exhibit the problems I'd been having.  This showed me it was a problem with the profile.  The booting into Windows was just out of curiosity to see if the profile problem persisted there... and before I could check, Google Desktop announced the broken file.

Weird that I have to defend my process of discovery here, but that was how it went down... I'm sorry it made it difficult for you, that wasn't my intention.  Though I may not have used a 100% logical "top-down" approach (sorry, mainly a right-brain kind of guy!), I do try to provide as much info as I can that is relevant to my problem.  And the fact that my profile folder is shared with Windows (the thing I guess you mean to say I neglected to disclose?) certainly seems to have had nothing to do with my problem.

All that said, I do appreciate your advice.  I never knew about starting an app from a terminal to view errors; I'll remember that next time.  Thanks for posting your thoughts on problem-solving in Linux; lots of good info in one place, and I appreciate that you took the time to share that with me.

Oh, and though I'm trying to stay away from Windows as much as possible just to see if I can, it is good for more than gaming... I'm a professional sound designer by trade, and to try to make a living using the tools currently available in Linux would be very difficult.  Same with video.  And though I've tried a few financial software solutions in Ubuntu, the closest I can come to the functionality of, say, Quicken (as bloated and twisted as it is), is Moneydance, but its online banking just isn't what I need it to be yet.  For those 3 things, it's Windows or Mac for me.  But for anything other than work and finances, I love Ubuntu!

Thanks to everyone who posted here, and TheWizzard, I will bookmark this for your Linux problem-solving info.  Much appreciated!

---

### Post by Straevaras on 2006-10-10
> **TheWizzard said:**
> nope. windows is good for gaming, nothing else! 

I second that.

Glad to see you got your problems fixe.  My first thought when I got that message is use the following command to view the process list:

```
ps aux
```

And look for any process associated with Firefox.  If you find any (in this case, I don't know if you would have), just type this:

```
kill xxxx
```

where the xxxx represents the process identication number.  Using "killall firefox" or "killall firefox-bin" probably should've worked, but I like to actually see what's running, just in case.  I know in Windows I've had problems in Firefox many times where the process didn't terminate completely and I had to go into task manager and manually terminate it.  I would get the same error you did after trying to re-open Firefox, too.  That's why I would think to check the process list first.

---

### Post by kalle314 on 2006-10-10
This thread might contain the solution:
[http://ubuntuforums.org/showthread.php?t=274672](http://ubuntuforums.org/showthread.php?t=274672)
(see post by grendelkhan)

---

### Post by mjpatey on 2006-10-10
Thanks, Straevaras.

Yeah, I did check running processes and saw none, and "kill" and "killall" didn't find any to kill.  It was truly a weird glitch, I assume caused by that corrupt "cookies.txt.moztmp" file.

-Mark

---

### Post by mjpatey on 2006-10-10
kalle314-

That was interesting, too.  I think my problem with "cookies.txt.moztmp" was similar to his problem with "lock"... FF was rudely terminated (I assume by my toddler's fascination with power buttons!), and the file was never automatically deleted as it would have been normally.

---

### Post by TheWizzard on 2006-10-11
@ mjpatey
don't take my comments too seriously. of course it is great if you find the solution for your problems. 
solving problems in linux with windows is just like... sort of asking for... well, i just couldn't resist to response to that. 

cheers

---

### Post by mjpatey on 2006-10-11
I know.  It was a happy accident, and I'm happy!  :-)

---

### Post by zcw100 on 2006-12-05
Try removing the .parentlock file. From your home directory...

$ cd .mozilla/firefox/
$ ls

you'll see three files pluginreg.dat profiles.ini and one with <8 random characters>.default

$ cd <8 random characters>.default
$ rm .parentlock

---

### Post by guyhome on 2006-12-16
I found a way to make it work, you just have to go delete or rename the .mozilla folder in your home directory, I think the problem is caused by a bad config file in this directory.

---

### Post by jim-fwb on 2006-12-29
> **TheWizzard said:**
> ```

killall firefox
```

this should do the trick.

remove & re-install are typical windows-reflexes. often not usefull in linux, only if you're sure you have dependency problems. rather than remove & re-install you can try removing the configuration folder (~/.mozilla/firefox).

You were right vis a vis my problem w/ firefox.  I'd tried removing and purging firefox with apt-get & removing the config file, then reinstalling firefox.  No dice.  Nor did "killall firefox" however, "killall firefox-bin" (posted elsewhere in this thread) worked just fine.  Box is an AMD64 running Kubuntu 6.10 for AMD64.  Thanks to all.

---

### Post by jamgalex on 2008-07-08
The problem has been caused by the computer generating two firefox profiles

This is so easy to resolve - simply go to your apps folder (ctrl+r then  type in %APPDATA% then delete the mozilla folder.

You will then find Firefox works perfectly

---

