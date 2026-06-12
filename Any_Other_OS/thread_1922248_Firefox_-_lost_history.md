---
title: "Firefox - lost history"
date: 2012-02-08
forum: Any Other OS
---

### Post by gelf12 on 2012-02-08
Hello

My first posting here!  :)

Firstly, I have a DELL Inspiron 530S Desktop with Linux Mint 10 installed and Firefox 7.0.1.

The problem is: switched on the pc today but found that 'History' (in Firefox) -> 'Show All History,' only 'Today's' searches were revealed - no previous record of the past days, weeks...!  

I can see no reason for this happening, except that I've had some trouble getting online recently via the ISP TalkTalk.  'Bookmark' hasn't changed.  I don't want to try anything myself to regain the History records because it might overwrite, and I'd lose everything.

Any advice, how to recover History?  In simple steps, please.

Thank you.

---

### Post by gelf12 on 2012-02-08
Hello:)

I have a DELL Inspiron 530S Desktop with Linux Mint 10 installed and Firefox 7.0.1.

The problem is: switched on the pc today but found that 'History' (in Firefox) -> 'Show All History,' only 'Today's' searches were revealed - no previous record of the past days, weeks...!  'Bookmark' hasn't changed.

I can see no reason for this happening, except that I've had some trouble getting online recently via the ISP TalkTalk (cold weather in UK?). I don't want to try anything myself to regain the History records because it might overwrite, and I'd lose everything.

Any advice, how to recover History? In simple steps, please.

Thank you.

---

### Post by nothingspecial on 2012-02-08
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by cariboo on 2012-02-08
Threads merged, please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by winh8r on 2012-02-08
> **gelf12 said:**
> Hello:)

I have a DELL Inspiron 530S Desktop with Linux Mint 10 installed and Firefox 7.0.1.

The problem is: switched on the pc today but found that 'History' (in Firefox) -> 'Show All History,' only 'Today's' searches were revealed - no previous record of the past days, weeks...!  'Bookmark' hasn't changed.

I can see no reason for this happening, except that I've had some trouble getting online recently via the ISP TalkTalk (cold weather in UK?). I don't want to try anything myself to regain the History records because it might overwrite, and I'd lose everything.

Any advice, how to recover History? In simple steps, please.

Thank you.

Not sure how they could have been deleted without you having changed something.

First go to Edit> Preferences> Privacy and check the settings there for history. If it is set to never remember thistory, thenn there is little you can do to get your history back.


If this is set to something other than Never remember history then do the following:

open your browser
in the address bar (NOT the search box!)  type about:cache and hit enter

this will take you to another screen where you will see a link that says List Cache Entries.

Click on this and you will see everything that is in the history.

Note that if the browser is set to never remember history , then all you will see in here is the history from the current session which will be deleted when you close the browser.

There were ways to recover history on old versions of firefox but these are now obsolete.

At least you have still got your bookmarks though!!


Just had another thought, you didn't by any chance follow someones advice when having problems connecting to the internet and go into about:config and delete any of the sql databases did you???:)

---

### Post by gelf12 on 2012-02-08
> **winh8r said:**
> Not sure how they could have been deleted without you having changed something.

First go to Edit> Preferences> Privacy and check the settings there for history. If it is set to never remember thistory, thenn there is little you can do to get your history back.


If this is set to something other than Never remember history then do the following:

open your browser
in the address bar (NOT the search box!)  type about:cache and hit enter

this will take you to another screen where you will see a link that says List Cache Entries.

Click on this and you will see everything that is in the history.

Note that if the browser is set to never remember history , then all you will see in here is the history from the current session which will be deleted when you close the browser.

There were ways to recover history on old versions of firefox but these are now obsolete.

At least you have still got your bookmarks though!!


Just had another thought, you didn't by any chance follow someones advice when having problems connecting to the internet and go into about:config and delete any of the sql databases did you???:)

Hello Winh8r

Thank you for replying.  As per your instructions:

Under, Edit>Preferences>Privacy found: Set to "FIREFOX WILL: REMEMBER HISTORY"

Typed-in CACHE

And, found:

Number of entries: 16406
Maximum storage size: 1048576 KiB
Storage in use: 1047933 KiB
Cache Directory: /home/...etc

And a long list of entries.

I must have exceeded the cache size then, and they were just dumped elsewhere?  Anything I can do now to recover/ put back any of it, or at least the most recent entries?

---

### Post by winh8r on 2012-02-09
First thing you can do is select all the entries in the list, copy them and paste them into an empty text file. At least that way you will be able to see them.
Will have a look at how to open the cache files, and post back here if I find anything.

If you do the above and save all entries to a file then you could clear your browser cache and free it up, which will doubtless speed up your browsing by a good bit.

Hope this helps you.

---

### Post by winh8r on 2012-02-09
I have had a quick look around and found that you can install a firefox add-on called SQLite manager which will allow you to manipulate databases.

go to tools> add-ons> and search for it
click install
restart firefox.

Now navigate to your home folder
/home
press ctrl +H (to display hidden folders)

find the folder named .mozilla
click on it
click on folder named abcd8xyz.default (the abc bit will be unique to your installation, just click on the folder with the .default extension)

locate the places.sqlite database.

this is where all browsing history and bookmarks are stored.

you can use the add-on you installed to navigate to this database and do whatever you want to do with your history.

Not much more I can do really but i hope this gets you a bit further.

Use a search engine and include specific terms in your search like:

firefox 7 + history + places.sqlite + Ubuntu

this will get you more relevant results.

Failing that it is probably best to ask the question on the Mozilla forums.

Good Luck

---

### Post by gelf12 on 2012-02-15
> **winh8r said:**
> I have had a quick look around and found that you can install a firefox add-on called SQLite manager which will allow you to manipulate databases.

go to tools> add-ons> and search for it
click install
restart firefox.

Now navigate to your home folder
/home
press ctrl +H (to display hidden folders)

find the folder named .mozilla
click on it
click on folder named abcd8xyz.default (the abc bit will be unique to your installation, just click on the folder with the .default extension)

locate the places.sqlite database.

this is where all browsing history and bookmarks are stored.

you can use the add-on you installed to navigate to this database and do whatever you want to do with your history.

Not much more I can do really but i hope this gets you a bit further.

Use a search engine and include specific terms in your search like:

firefox 7 + history + places.sqlite + Ubuntu

this will get you more relevant results.

Failing that it is probably best to ask the question on the Mozilla forums.

Good Luck

Because I had apparently overloaded the cache, I decided it would just be better to empty the cache and start again without trying to save anything!  However, I found by going, Tools > Clear Recent History > Cache, if I only clear the Cache, and then look back at, 'about:cache' it has been cleared.  Then look at, History > Show All History, the sites visited are still there!  Is this a solution that doesn't slow the pc down, by keeping the cache clear, and yet keeping the History? :)

---

