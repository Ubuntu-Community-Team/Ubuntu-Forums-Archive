---
title: "Ubuntu, Kontact, and Palm(pilot) hotsync - how?"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by twrock on 2006-11-29
I have given up on my Palm TX synchronizing with Evolution via gpilot. I even did a fresh install of Kubuntu in an attempt to get some kind of synchronization working consistently. (But I had serious problems with network printing via Samba, so I switched back to Ubuntu (Dapper) where that worked without a hitch.) I have read posts from a number of people who really like Kontact as a PIM, so I am hoping to use Kontact instead of Evolution.

I'd like to at least get things started right. Since I am using the GNOME desktop but trying to sync with a KDE app, which sync conduit should I be using, kpilot or gpilot? (Please tell me kpilot, because I don't have any hope that I can get gpilot to work.) Has anyone else been sucessful in getting a consistent hotsync using Kontact in Ubuntu? Any pointers from anyone?

---

### Post by alaaji on 2006-11-29
I was having problems syncing my palm zire with gpilot.  Here's what I did.  Go to System > Preferences > Palm OS devices.  Under the PDA tab, highlight the name for your pda and click edit.  Under pda identification, click "get from pda."  After it retrieves your info by hotsyncing, you click the hotsync button again on your pda and it works.  Unfortunately, you will have to do that everytime that you reboot your computer.  It's a pain but it's a work-around.

---

### Post by twrock on 2006-11-29
Thanks for that tip. I wasn't aware of that work-around.

My problems with gpilot were that I could get one hotsync to work after a fresh setup of gpilot and the Pilot Applet, but never more than once. I don't know if your tip would solve that problem, but if I can't get Kontact sychronization working, I'll definitely give it a try.

---

### Post by Spin Doctor on 2006-11-30
> Under the PDA tab, highlight the name for your pda and click edit. Under pda identification, click "get from pda." After it retrieves your info by hotsyncing, you click the hotsync button again on your pda and it works. Unfortunately, you will have to do that everytime that you reboot your computer. It's a pain but it's a work-around.I found this reconnect solution myself a couple of weeks ago. I later found a way to tweak it even better... =) If you use a laptop that  supports "sleep" poweroption, you dont have to shutdown your computer completely every time. 

People now could argue that this will still consume power..which it does litte...but goahead and disconnect the power and let it run on the battery. It could run on days depending on your battery.

What I have configured Ubuntu to do is when I close my screen it automatically goes inte sleepmode. Then I unplugg my powercable. When I want to use it it again, I raise my screen, and I have to just log in to Ubuntu, and my system is up an running within 4 seconds. 

This way I also dont have to do this reconnect work around every time I want to sync after a complete shutdown. An added bonus, is that I dont either have to enter my password to get my WPA password for my accesspoint. It will reconnect to my wireless network right on by itself...just like it should =)

However, does anyone know how to fix this issue with the palmpilot losing its settings for some reason after every complete restart of Ubuntu.There should be someone out there with handheld palm sync skills beyond mine =) Now my alternative solution works great, but I always want a "real" solution =)

---

### Post by twrock on 2006-12-01
(It's lunchtime at work and I'm using a Windows machine, so I might not get this exactly right but....)

Seems like a lot of people have problems with Ubuntu and Palm synchronization. Now if each of us had the same problem, I'm sure the solution would already exist. But, alas, it doesn't seem to be that easy.

Last night I decide to give Evolution one more try. I wasn't seeming to get any "bites" on my question about Kontact, so I tried to set up gpilot once again for Evolution. But this time, I went through Evolution to do it. In one of the menus there was a "Synchronize ..." button. I just clicked on that and followed the directions. At one point it told me to connect my Palm and hit the hotsync button. I did, and it worked. Well, I had gotten that far before, so I wasn't ready to declare success just yet. 

I added the Pilot Applet to the taskbar, and it worked yet again! I set up the conduits, and it still worked. But it didn't sync my addresses until I set the conduit to have the Palm overwrite the desktop once ("copy from..." was the setting I think). So I thought I had finally pulled it off. 

However, after shutting down Evolution, things started going astray. It wouldn't sync anymore. I opened up system monitor and killed gpilotd and the pilot applet and tried again. I got it working again by loading the Pilot Applet.

So I decided to reboot and see what happened. Success! It still worked. But only until I started Evolution again. Then things started to hang up.

I needed to get some sleep, so I went off to bed. This morning I only had enough time to reboot and sync (success), then load Evolution and try again (failure). So just maybe I have a pattern to my problem, but I won't know without further experimentation. But at least I do have a little hope that I can get it to work, if only a little.

---

### Post by Spin Doctor on 2006-12-01
Sounds like you have something to work on there. Are you connecting your palm trough an usb hub or directly into one of your computer usb slots?

---

### Post by Spin Doctor on 2006-12-01
You know what! I think I read somewhere here on the forums that there is a bug in the kernel used for Dapper that makes palm syncronization fail. Maybe someone with more knowledge about this could confirm or deny this.

I guess upgrading to Edgy could be part of solving your problem if my memory serves me right!

---

### Post by twrock on 2006-12-01
I'm connected directly through one of my onboard USB ports.

I am getting something that resembles success, but not every time. At this point, every time I have done a reboot, it works well. (So unlike the problems others are having, mine seems to be solved by rebooting not caused by it.) But after opening and closing Evolution, things start to get flakey. I haven't gotten an exact pattern figured out, so I'm not able to ask any more of a specifc question. I honestly don't even really know where to look at this point.

I will say that there does seem to be a very long delay while the Palm says that the user is being identified. Sometimes this is the point at which it hangs. At other times it never seems to even start to make any connection (no musical beep indicating the hotsync has started).

Regarding Edgy, I did that once already, but not to solve my hotsync problems. I reverted to Dapper (via fresh install) because I had other problems introduced by Edgy that I never had in Dapper. I'd like to avoid the upgrade because of that. 

I'd really like to be able to get all of these little quirks with Linux figured out and fixed. It is unlikely that I will stop using Windows at the office any time soon, but I made a "commitment" to stop using Windows (and other non-open-source software) on my new home machine. But I do wish that things "just worked" in Ubuntu instead of all these little "issues".

Thanks for the ideas.

---

### Post by frrobert on 2006-12-02
I couldn't get my palm to work with Evolution either but it worked great with j-pilot.  You may want to give that a try

---

### Post by JAPrufrock on 2006-12-03
I can get my palmone to work with gpilot and evolution, or with the pilot applet. However, the only time it works consistently is when I synchronize right after startup or after a re-boot or restart.

---

### Post by twrock on 2006-12-03
Sounds quite similar to my problems at the moment.

Things are much better for me this time around than the first time I tried to get all this working. I can now get multiple successful sync's before a failure. I more specifically described the pattern over in another thread: [http://www.ubuntuforums.org/showthread.php?t=286102](http://www.ubuntuforums.org/showthread.php?t=286102)

Since I am now working on getting gpilot and Evolution to work again, I though it made sense to reply to that post (which is specifically about getting a Palm TX to sync with Dapper, not using Kontact as an alternative).

If anyone can get things to consistently deliver the same results, good or bad, then there is something to work with. Unfortunately seems we all have different symptoms. Maybe it is time to try the upgrade to Edgy again. Some have said that the problems with Palm sync are solved there. Unfortunatly Edgy gave me a whole new set of problems last time I tried it.

---

### Post by Spin Doctor on 2006-12-03
> **twrock said:**
> ...Maybe it is time to try the upgrade to Edgy again. Some have said that the problems with Palm sync are solved there. Unfortunatly Edgy gave me a whole new set of problems last time I tried it...

You lose some you win some =)

---

### Post by twrock on 2006-12-03
Ok, I had some time, so I took the plunge once again! Since I had gotten some of the Edgy problems worked out last time, I thought I'd give it another try to see if it really would solve my Palm hotsync problems. It seems to have worked! Below is my very lengthy record of my experience, in "graphic" detail for anyone with enough time and patience to wade all the way through it. I will also post it to the other thread about these issues in the hopes of helping a few others. (Now back to trying to solve that crazy extra floppy drive that appears out of nowhere in Edgy.)

_______________________________________________________

Report on my process of getting a Palm TX to hotsync with Evolution via gnome-pilot in Ubuntu Edgy Eft (6.10):

After installing Edgy and completing the first update, I decided to try to get my Palm TX hotsync working. These are the steps I took.

(Background note: My install of Edgy was "clean"; I formatted all partitions so no configuration information was carried over. During my install of Edgy, I had my Palm TX plugged into the original Palm hotsync cable. I doubt that mattered at all, but I'm trying to make this as accurate a description of what I did as possible.)

After installing Edgy, I ran Evolution for the first time. I set up a default email account, but I did not check email or do anything else. I closed Evolution.

I then started the Palm OS Devices configuration by clicking System> Preferences> PalmOS Devices. I then just went through the menu prompts as follows:
   Device Settings:
      Name: Cradle
      Type: Changed to USB
      Timeout: 2
      Device: /dev/pilot
      Speed: 57600
   PDA Identification: "Yes, I've used sync software with this PDA before."
   Initial Sync: Put the PDA in the cradle (actually, just connected the cable) and pushed hotsync button. 
      Results: Successfully retrieved Owner Name and ID from PDA.
               Owner Name: *** ******** (my PDA username)
               PDA ID: 3837
   PDA Attributes:
      Name of PDA: Palm TX
      Local folder: /home/ron/Palm (I had already created this folder manually, so I don't know what would happen if I hadn't.)
   Success (I clicked "Apply")

gnome-pilot Settings popped up. Under the Conduits tab, I enabled the following:
   Backup (the directory was already set; I clicked "Remove local base if deleted on PDA")
   eAddress
   eCalendar
   eMemos
   eToDo
   Expense (I set the directory to /home/ron/Palm/Expense which was a folder I had already created.)

   NOTE: I also set all "One time action:" to "Copy from PDA" and checked "Sync Private Records" in each item I had enabled (that had that as an option).

I closed gnome-pilot.

I hit the hotsync button on my Palm cable. I heard the musical beep, and the hotsync began. Nothing popped up on my computer screen at all; the only indication that anything was happening was that I could see on the PDA screen that things were synchronizing. It took some serious time to back up all my Palm apps (I have a lot of apps and data!).

SUCCESS!!!

However, interestingly, my "Expense" folder was somehow moved into a newly created folder named "del". I don't know where it came from nor why "Expense" was moved there.

I opened Evolution. I clicked on the "Contacts" tab and I got an error message saying that Evolution was not able to access its data file. Calendar, Memos, and Tasks were all there just fine. I closed Evolution and reopened it. Still no Contacts, but everything else was still fine. I closed Evolution.

I reopened PalmOS Devices (gnome-pilot Settings). I clicked on the Conduits tab and set the "One time action" in eAddress to "Copy from PDA". I closed gnome-pilot Settings. I hit the hotsync button on my cable. My Palm TX tried to start a hotsync and quickly did a reset. Bummer! I waited for it to reset. I again hit the hotsync button. It started to hotysync. This time the hotsync went much quicker.

I opened Evolution. Success! My Contacts were all there. I closed Evolution. I wanted to test to see if opening and closing Evolution would affect gnome-pilot negatively in Edgy as it had in Dapper.

I hit hotsync again. Again the sync was successful and as quick as the last time (maybe slightly quicker because it didn't have to sync all those addresses).

I opened the file browser to have a look at my Palm folder again. What's this? The Expense folder has returned and has files in it. The same files are still in the /Palm/del/Expense folder. Hmmm, I don't know what's up with that, but I don't think it is a problem. At least it is there, not gone.

I made a minor change to a record in each of my main PIM apps and tried to sync again. It sync'ed.

I opened Evolution and verified that all the changes had synchronized. They had, and there the Expense entry showed up in the Expense folder as well.

I made a change in a Contact in Evolution and started another hotsync with Evolution open. It sync'ed again, but the changed Contact did not seem to change (I had changed the "File under" only, so maybe that doesn't really sync across). I made a more significant change (Country) and synced again. This time the change did get sync'ed over. Looks good!

I closed Evolution and hit hotsync again. Success.

I restarted the gnome desktop (Ctrl-Alt-Backspace). Hit the hotsync button. Nothing. Started Evolution. Hit the hotsync button. Nothing.

Right clicked on the bottom panel and added Pilot Applet to the panel. Hit hotsync. The "gnome-pilot progress" dialog popped up, and for the first time ever (including when I was using Dapper) information about the progress was displayed in the window. Great!

Opened Evolution. Hotscyn'ed. Success.

Closed Evolution. Hotsync'ed. Success.

Restarted gnome desktop. Pilot Applet was still in the panel. Hotsync'ed. Success.

At this point, I have done multiple hotsync operations with Evolution both open and closed. I have made data changes and verified that they sync'ed. I think I have a consistently working Palm TX synchronization.

So, if synchronization is a critical function for you and you are having problems in Dapper (or earlier versions), you might seriously consider an upgrade to Edgy. However, I should emphasize that I did a complete install of Edgy from scratch (reformatted all partitions).

YMMV. Good luck.

---

### Post by Spin Doctor on 2006-12-03
How great is not the flavor of success? I am glad u got it to work finally..
Great job man!

---

### Post by twrock on 2006-12-03
Thanks. Yeah, it does feel good. My Palm is extremely important to me, and I recently had to explain to a friend that I didn't know if Linux was a real option for me because I couldn't get a hotsync to work consistently. But it looks like that one is solved!

---

