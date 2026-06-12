---
title: "Home file seems to be empty"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Eric Weir on 2007-09-19
Again, I'm a rank beginner with Ubuntua and Linux. I think I may have done something fatal -- i.e., the machine runs, but I may not be able to use it. Reason for my suspicion:

In a post a couple days ago I said that I was unable to copy my Firefox bookmarks from the Windows machine I'm transitioning from to the /etc/firefox/profile folder on my Ubuntu machine. Subsequently I noticed that my /home/eric folder contained a mozilla folder with a folder that contained a recent copy of the current bookmarks. I figured that was where I should put the bookmarks from the Windows machine. 

Before I could do so, though, I noticed that the home folder contained an eric folder, and that the eric folder contained everything that was in the home folder minus itself. Seeing no need for such duplication, I deleted the eric folder. Now my home folder contains only three items, an autosave folder, a desktop folder, and an examples folder. The mozilla folder that I was going to copy the Firefox bookmarks to, and many others, is gone. And the eric folder in the trash also contains only these three items.

What have I done? Is there anyway to recover? Or is this the way it's supposed to be?

Please help. I'm desperate.

---

### Post by Dylock on 2007-09-19
ouch well /home/eric was the home directory for the account eric

how exactly did you delete it using Nautilus or command line?

---

### Post by mysticmatrix on 2007-09-19
> **Eric Weir said:**
> Again, I'm a rank beginner with Ubuntua and Linux. I think I may have done something fatal -- i.e., the machine runs, but I may not be able to use it. Reason for my suspicion:

In a post a couple days ago I said that I was unable to copy my Firefox bookmarks from the Windows machine I'm transitioning from to the /etc/firefox/profile folder on my Ubuntu machine. Subsequently I noticed that my /home/eric folder contained a mozilla folder with a folder that contained a recent copy of the current bookmarks. I figured that was where I should put the bookmarks from the Windows machine. 

Before I could do so, though, I noticed that the home folder contained an eric folder, and that the eric folder contained everything that was in the home folder minus itself. Seeing no need for such duplication, I deleted the eric folder. Now my home folder contains only three items, an autosave folder, a desktop folder, and an examples folder. The mozilla folder that I was going to copy the Firefox bookmarks to, and many others, is gone. And the eric folder in the trash also contains only these three items.

What have I done? Is there anyway to recover? Or is this the way it's supposed to be?

Please help. I'm desperate.

Cool Stuff. Well, your HOME folder was actually /home/<username>. :( 
So its like deleting C:\Users and DOcuments\<userNAme>\My Documents because it contains similar stuff to My documents you use :).

Now if your machine is still running, good. You have lost your entire data, but some how Ubuntu manages to run by restoring default settings. Start all your applications once again, and they will start as if NEW, creating their default setting once agin under your HOME.

Next, if computer is refusing to start, post the errors here. Someone would be able to help you.

---

### Post by Eric Weir on 2007-09-19
> **Dylock said:**
> ouch well /home/eric was the home directory for the account eric

how exactly did you delete it using Nautilus or command line?

With Nautilus. 

I thought I remembered eric being the only subfolder under /home, but as I said, /home had everything /home/eric had in addition to eric. I figured if I deleted eric, all that other stuff would still be there.

Again, help appreciated.

---

### Post by Dylock on 2007-09-19
ok you used nautilus good
go into nautilus and look for trash
you should be able to restores your directory from there

---

### Post by Eric Weir on 2007-09-19
> **mysticmatrix said:**
> Cool Stuff. Well, your HOME folder was actually /home/<username>. :( 
So its like deleting C:\Users and DOcuments\<userNAme>\My Documents because it contains similar stuff to My documents you use :).

Yeah, I understand NOW. I wouldn't have deleted it if /home hadn't had everything that /home/eric had. 

> Now if your machine is still running, good. You have lost your entire data, but some how Ubuntu manages to run by restoring default settings. Start all your applications once again, and they will start as if NEW, creating their default setting once agin under your HOME.

I have rebooted since, without any problem.

Thanks for the info and the suggestions.

Sincerely,

---

### Post by Dylock on 2007-09-19
another post, if your using the default gnome session from the ubuntu install you should also be able to find it in the 'Places' menu or whatever its called. Im not at my linux box right now to confirm specifics but there definitly is a way to get to 'trash'

---

### Post by Eric Weir on 2007-09-19
> **Dylock said:**
> ok you used nautilus good
go into nautilus and look for trash
you should be able to restores your directory from there

Nope. That's the first place I went. There's a copy of eric, but all it has are the same three items that are in /home.

I didn't empty the trash, either.

Thanks,

---

### Post by Eric Weir on 2007-09-19
> **Dylock said:**
> another post, if your using the default gnome session from the ubuntu install you should also be able to find it in the 'Places' menu or whatever its called. Im not at my linux box right now to confirm specifics but there definitly is a way to get to 'trash'

Don't have trash in places, but there's a trash icon on the desktop. As I say, it's got a copy of eric, but the only thing in it is the three items that are in /home.

Just curious -- it's not gonna help solve the problem now -- but why did /home have -- or appear to have -- a copy of everything that was in /home/eric?

Regards,

---

### Post by Dylock on 2007-09-19
my guess would be those files are settings global to all users

then the files that are in the /home/eric are config files for the user eric only

---

### Post by sailor2001 on 2007-09-19
in places/home if you ctrl/h you would find the trash folder with whatever you deleted

---

### Post by Dylock on 2007-09-19
> **Eric Weir said:**
> Don't have trash in places, but there's a trash icon on the desktop. As I say, it's got a copy of eric, but the only thing in it is the three items that are in /home.

Just curious -- it's not gonna help solve the problem now -- but why did /home have -- or appear to have -- a copy of everything that was in /home/eric?

Regards,

if your looking to restore that directory, thats it, and that was the content of the directory when it was deleted.

now if you had stuff in there that isn't showing up in the deleted directory, there might be a different problem

---

### Post by Eric Weir on 2007-09-19
> **mysticmatrix said:**
> 
Now if your machine is still running, good. You have lost your entire data, but some how Ubuntu manages to run by restoring default settings. Start all your applications once again, and they will start as if NEW, creating their default setting once agin under your HOME.

I've opened quite a few applications, and there's still nothing in /home -- except the three irrelevant folders I've mentioned.

What do I do know -- reinstall?

Thanks,

---

### Post by Eric Weir on 2007-09-19
> **Dylock said:**
> if your looking to restore that directory, thats it, and that was the content of the directory when it was deleted.

now if you had stuff in there that isn't showing up in the deleted directory, there might be a different problem

There was a lot of stuff in it, like the /home/mozilla/firefox folder. I guess it was all the configuration data for all my applications. 

One other thing, if it makes any difference: I believe the /home/eric that I deleted was a link -- it had that little arrow on it -- that had originally been on the desktop, and that I'd deleted several days ago and then restored, because I was nervous about having deleted it. 

Does the fact that it was a link, if it was, make any difference? Whatever it was, it was the only copy of eric in /home.

---

### Post by Eric Weir on 2007-09-19
> **sailor2001 said:**
> in places/home if you ctrl/h you would find the trash folder with whatever you deleted

Hmm. I tried this. I didn't find the trash folder, but THE MISSING FILES REAPPEARED!

Well, a lesson learned. Don't, no matter what, delete /home/eric!

Still curious -- why did /home have a copy of everything that was in /home/eric? 

Thanks for the lifesaving suggestion. 

Regards,

---

### Post by Eric Weir on 2007-09-19
> **sailor2001 said:**
> in places/home if you ctrl/h you would find the trash folder with whatever you deleted

As I reported in my last post, when I did ctrl/h in /home/eric, the missing files showed up. However, when I closed Nautilus and reopened it, the missing files were missing again. And again, ctrl/h caused them to reappear.

Also, I copied the Firefox bookmarks from my Windows machine into /home/eric/.mozilla/firefox/gd2viden.default, which I take it is my Firefox profile. However, when I opened Firefox, the bookmarks failed to show up. I tried to import them from within Firefox, browsing the import window to the profile folder. However, I could get no further than /home/eric, and again the only folders displayed there were the three I mentioned earlier. And ctrl/h did not in the import wizard.

I can get the missing files to show up in Nautilus, but the system doesn't seem to recognize them. 

How can I get my files back, really, permanently?

Thanks,

---

### Post by t0p on 2007-09-19
This reminds me of the time when I decided to "make the most" of my disk space" by deleting everything I* thought* I didn't need.

Notice the stress on *thought* - I'd been using Linux for a few months, thought I knew it all, and deleted files basically by judging them on their names!  When permission was denied to delete, I sudoed it, cos I knew best... and in a short space of time I managed to reduce my Ubuntu to a quivering vegetable!!

I learned a useful lesson that day - don't delete stuff unless you're *sure* you don't need it.  And if you gotta use sudo to delete it, make double, triple, quadruple... all the way to infinitely sure it needs deleting.  That's the key really - **don't delete stuff unless you actually need to get rid of it!**  Disk space is so cheap and plentiful nowadays, why get rid of stuff?

Oh, and back up, *back up*, ***back up***, **B A C K  U P ! ! !**

---

### Post by Eric Weir on 2007-09-19
> **Eric Weir said:**
> As I reported in my last post, when I did ctrl/h in /home/eric, the missing files showed up. However, when I closed Nautilus and reopened it, the missing files were missing again. And again, ctrl/h caused them to reappear.

I"m getting the impression that this is the way it's supposed to be. The program-related files in /home/eric are not displayed -- I gather -- by default. 

> Also, I copied the Firefox bookmarks from my Windows machine into /home/eric/.mozilla/firefox/gd2viden.default, which I take it is my Firefox profile. However, when I opened Firefox, the bookmarks failed to show up.

About this I'm embarrassed. The reason my old bookmarks weren't showing up was because I was copying the backup of the bookmarks from the Ubuntu machine. When I realized that and copied the bookmarks from the right disk, they showed up when I started Firefox. 

I'm learning, verrry slowly. 

And thanks for the suggestion about ctrl/h.

Sincerely,

---

