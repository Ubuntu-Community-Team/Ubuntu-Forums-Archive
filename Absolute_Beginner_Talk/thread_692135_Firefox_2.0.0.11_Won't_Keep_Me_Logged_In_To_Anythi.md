---
title: "Firefox 2.0.0.11 Won't Keep Me Logged In To Anything"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Teasdale on 2008-02-09
I even changed my settings to "accept all cookies," and then I cleared my cookies, closed down everything and re-opened a new browser. I signed in to a site, closed down, and when I re-opened a browser, it wants to me to login again! It doesn't remember any sites I've been to. It acts like this is the first time it's seen the site. And it seems to be all sites.

This just started yesterday. The only thing I've changed is that I installed all the updates that Ubuntu wanted me to install.

---

### Post by sports fan Matt on 2008-02-09
just a dumb question, did you also install the firefox update to 2.0.0.12?

---

### Post by Teasdale on 2008-02-09
I pretty much let the install manager update everything. I just installed Ubuntu 7.10 a week ago, and there were hundreds of updates it wanted to do right off the bat, but I waited a week and then finally yesterday let it do the updates.

Wait - are you asking if it installed the 2.0.0.12 update to my 2.0.0.11 version? I don't know, how would I check? When I click my "about" in Firefox, it says I have 2.0.0.11.

---

### Post by y-lee on 2008-02-09
One thing you can try

[LIST]
[*]Open a new tab in FF
[*] In the URL window, type **[noparse]about:config[/noparse]**
[*]Go down the list in the window to **network.cookie.cookieBehavior**
[*]To stop blocking third party cookies be sure this setting is "0". Double click it to change
[*]Close tab up.
[/LIST]

---

### Post by mikewhatever on 2008-02-09
> **Teasdale said:**
> I even changed my settings to "accept all cookies," and then I cleared my cookies, closed down everything and re-opened a new browser. I signed in to a site, closed down, and when I re-opened a browser, it wants to me to login again! It doesn't remember any sites I've been to. It acts like this is the first time it's seen the site. And it seems to be all sites.

This just started yesterday. The only thing I've changed is that I installed all the updates that Ubuntu wanted me to install.

Every time you delete cookies, you'll have to login again. Either accept them, or don't, but make exceptions. You can lso make Firefox remember passwords in Security tab.

---

### Post by sports fan Matt on 2008-02-09
yeah there was an update to firefox yesterday to 2.0.0.12..to check is very easy:) System>Adminstration> Update manager and see if that fetches the update manager..if that does not work you can run (in terminal) Applications>Accessories>Terminal this command: sudo apt-get update and see if this fetches it...

Sometimes the updates can be sneaky to catch :)  Hope this helps..  Also try y-lee's suggestions as well

---

### Post by Teasdale on 2008-02-09
> **y-lee said:**
> One thing you can try

[LIST]
[*]Open a new tab in FF
[*] In the URL window, type **[noparse]about:config[/noparse]**
[*]Go down the list in the window to **network.cookie.cookieBehavior**
[*]To stop blocking third party cookies be sure this setting is "0". Double click it to change
[*]Close tab up.
[/LIST]

I did that. It is set to zero.

---

### Post by p_quarles on 2008-02-09
> **Teasdale said:**
> I did that. It is set to zero.
It sounds like the settings are all correct. You mentioned you haven't installed anything recently, but is it possible that you're using any kind of anonymization software? I once ran into something very similar when using the Stealther plugin for Firefox, and had simply forgotten that I left it on. Using something such as TOR could have a similar effect. Possible?

The other thing to do here would be to use a different browser and seeing if you have the same problem. That would at least point to where the problem exists.

---

### Post by y-lee on 2008-02-09
Ok

type in a terminal

 ```
firefox  -P 
```

now create a new profile, see [Firefox help ]("http://www.mozilla.org/support/firefox/profile#new")if ya need more info.

See if the new profile has the same problem. If not some add on or some thing in your old profile is causing your problem.

---

### Post by y-lee on 2008-02-09
Also it might be a dumb question but you don't have **always clear my private when i close firefox** checked do ya (under preferences -->Privacy ) ?

---

### Post by Teasdale on 2008-02-09
I've updates to Firefox 2.0.0.12.

I don't have "always clear my private when i close firefox" checked.

I'm accepting all cookies, no questions asked. I have Firefox checked to remember all sites I visit for 9 days.

I've restarted my computer. Went to a site and signed in, checking "remember me." Closed all browsers, opened a new browser, and it hadn't remembered that I went to that site. Firefox still isn't remembering any sites I go to.

I'll try a new profile.

---

### Post by Teasdale on 2008-02-09
> **y-lee said:**
> 
type in a terminal

 ```
firefox  -P 
```


This opens a new Firefox browser.

> **y-lee said:**
> 
now create a new profile, see [Firefox help ]("http://www.mozilla.org/support/firefox/profile#new")if ya need more info.

I've tried various ways of finding the directory with the information on the page, I can't figure out what to type into the terminal to create a new profile.

home/Teasdale/.mozilla/firefox/
~/.mozilla/firefox/Teasdale.default/
it doesn't like these.

/home/Teasdale/.mozilla/firefox/ 
This is a directory, but it didn't open a new profile, it just informed me that, 'Yes, this is a directory.'

But
/home/Teasdale/.mozilla/firefox/-P
and
/home/Teasdale/.mozilla/firefox/-ProfileManager
/home/Teasdale/.mozilla/firefox/ProfileManager
aren't directories.

---

### Post by y-lee on 2008-02-09
type ** firefox -P**

that should give you the option of creating or using another profile.

---

### Post by Teasdale on 2008-02-09
> **y-lee said:**
> type ** firefox -P**

that should give you the option of creating or using another profile.

It opens another Firefox browser and displays the website I have set as my homepage. I don't see any options to create a new profile, it looks exactly like my regular homepage.

firefox -Profile 
does the same thing - opens a new browswr page.

---

### Post by Teasdale on 2008-02-09
I installed kazehakase, a browser I've never heard of. It *does* remember the sites I've been to, although it won't let me import my bookmarks.

---

### Post by y-lee on 2008-02-09
Installing another browser is great I use several myself But it has not fixed your problem. Firefox is still broke as far as I know. If it is not your profile then perhaps it is a permission issue.  :confused:

btw [Swiftweasel]("http://swiftweasel.tuxfamily.org/") is a faster version of firefox which will import both your bookmarks and your profile. Of course if your profile is messed up then swiftweasel would still act the same way as firefox. 

Anyway good luck.

---

### Post by y-lee on 2008-02-09
> **Teasdale said:**
> It opens another Firefox browser and displays the website I have set as my homepage. I don't see any options to create a new profile, it looks exactly like my regular homepage.

firefox -Profile 
does the same thing - opens a new browswr page.

Ya could try

```
firefox -ProfileManager  
```

Altho that is not typical firefox behavior ya describe above :confused:

Has me wondering what the heck is going on? :lolflag:.

---

### Post by sports fan Matt on 2008-02-09
I agree..swiftweasel is faster then Firefox because of optimization and its very easy as was said to import your bookmarks...

---

### Post by y-lee on 2008-02-09
> **sox fan Matt said:**
> I agree..swiftweasel is faster then Firefox because of optimization and its very easy as was said to import your bookmarks...

yep. [ Wikipedia]("http://en.wikipedia.org/wiki/Swiftweasel") explains it quite well. :)

It is also very easy to install as ya just download a deb for your system. I use it instead of firefox tho I have FF on my system, two of them actually,  being a dapper user I have to have FF 1.5 plus I always compile the current one.

---

### Post by Teasdale on 2008-02-09
If it imports my profile, then it will likely import the same problem. I read that kazehakase has some security issues, so I've installed Opera and I'll see if that works better.

It's funny, but last week when I had WinXP, my Mozilla browser wasn't remembering certain sites I'd visited - it remembered some, but there were a couple that it would never, never remember - like google/igoogle. I thought I'd get rid of that problem when I did a clean install of a totally new OS - but here I am, and Firefox remembers nothing at all!

---

### Post by y-lee on 2008-02-09
> If it imports my profile, then it will likely import the same problem. I read that kazehakase has some security issues, so I've installed Opera and I'll see if that works better.

Yeah it might import the same problem if it is your addons causing the problems than again it might not. Options in add ons were NOT imported for me, the addons were but i had to go thru all that had options and reset them. No harm in trying it easy to install and should be easy to uninstall.

Opera is a great browser, in some ways bettern firefox. And I'm a big firefox believer so for me to say that means something. However I've got to have all my firefox extensions, can't live without them  :lolflag:

If ya wanna fix firefox keep posting here and we will fix it in time. I'm sure i could fix it if I were there, but I could be wrong. Anyway good luck and try the profile manager thing above or disable or uninstall all  your add ons. They might be the problem.

---

### Post by Teasdale on 2008-02-09
I guess I'll keep trying to fix Firefox. Opera won't let me sign in to blogger - I'm in, but it keeps bringing me to the sign-in page so I'm thinking that blogger doesn't support Opera.

I'll look into Swiftweasel - I didn't see it in my Ubuntu Add/Remove programs list, so I wondered if it would be difficult to install (repositories and other terrifying unknowns might be required!)

---

### Post by y-lee on 2008-02-09
Swiftweasel should be easy to install it is not in the repos but found at [source forge]("http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717&release_id=575236"). 

They have a deb for 2.0.0.11 version which might be the easiest to install. With swiftweasel you have to pick out the right version for your computer, see [which build ]("http://swiftweasel.wiki.sourceforge.net/Which+Build%3F")if this confuses you. 



> Opera won't let me sign in to blogger - I'm in, but it keeps bringing me to the sign-in page so I'm thinking that blogger doesn't support Opera

That is odd, I don't know anything about blogger but that doesn't sound right to me.

Anyway have you tried the profile manager thing yet, not capitalization is important...i think at least. lol

```
firefox -ProfileManager
```

---

### Post by LookTJ on 2008-02-09
> **Teasdale said:**
> It opens another Firefox browser and displays the website I have set as my homepage. I don't see any options to create a new profile, it looks exactly like my regular homepage.

firefox -Profile 
does the same thing - opens a new browswr page.
You have to close the firefox browsers(I mean every window of firefox) then type firefox -ProfileManager

---

### Post by y-lee on 2008-02-09
> **Taylor said:**
> You have to close the firefox browsers(I mean every window of firefox) then type firefox -ProfileManager


Good catch I hadn't even thought about somebody doing that but I can see it now. thanks :)

---

### Post by Teasdale on 2008-02-09
> **Taylor said:**
> You have to close the firefox browsers(I mean every window of firefox) then type firefox -ProfileManager

That worked! I've created a new profile, I'll see if I still have the problem.

---

### Post by Teasdale on 2008-02-09
The new profile appears to be remembering where I've been, so far, anyway.

What does "never remember passwords" mean in Firefox? I thought that clicking it meant that when I login to sites, I'd have to manually put in the password myself. Could it mean that Firefox won't remember that I've been there and make me login to sites even if I check the "remember me" box at the site?

I'll try to get back into the other profile and change that setting and see.

---

### Post by Teasdale on 2008-02-09
> **Teasdale said:**
> 
What does "never remember passwords" mean in Firefox? I thought that clicking it meant that when I login to sites, I'd have to manually put in the password myself. Could it mean that Firefox won't remember that I've been there and make me login to sites even if I check the "remember me" box at the site?.

That's not it. I even clicked the box "remember password for this site" when it came up, and when I went back to the site in a new browser, it wanted me to login all over again.

So it must be something that happened in my old profile.

I'd make a note never to do it again if I knew what I had done to cause the problem. The new profile seems to be working fine.

---

### Post by Chuck Dynamite on 2008-02-15
I was having the same problem up until a few minutes ago actually, had nothing to do with updates, it was just a simple setting that I kept overlooking. Tools> Options> Security> and then make sure that it's set to accept all AND "keep until: they expire"

Looks like you got it working though.

---

