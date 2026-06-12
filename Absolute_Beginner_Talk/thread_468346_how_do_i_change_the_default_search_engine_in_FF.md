---
title: "how do i change the default search engine in FF?"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by thesonisshining on 2007-06-08
i don't want to use google. i would rather use ask.com. is there any way to change me default search engine, and if so; how?#-o

---

### Post by NeoLithium on 2007-06-08
On then little search engine window, click the down arrow by the google icon, and select 'Manage Search Engines'  then click "Get more Search Engines" on the window that pops up :)

---

### Post by thesonisshining on 2007-06-08
> **NeoLithium said:**
> On then little search engine window, click the down arrow by the google icon, and select 'Manage Search Engines'  then click "Get more Search Engines" on the window that pops up :)

i have it in my search box but i want FF to search through ask.com when i type stuff in the address bar. any ideas

---

### Post by NeoLithium on 2007-06-08
> **thesonisshining said:**
> i have it in my search box but i want FF to search through ask.com when i type stuff in the address bar. any ideas

You bet.
Create a new bookmark, name it what you like.  in the location put:
```

http://www.ask.com/web?q=%s

```
And put the keyword as ```
a
```

Then the address bar will use it, ie: 
```

a what I'm searching for 

```
Will search ask.com for 'what I'm searching for'

---

### Post by thesonisshining on 2007-06-08
> **NeoLithium said:**
> You bet.
Create a new bookmark, name it what you like.  in the location put:
```

http://www.ask.com/web?q=%s

```
And put the keyword as ```
a
```

Then the address bar will use it, ie: 
```

a what I'm searching for 

```
Will search ask.com for 'what I'm searching for'

it didn't work:(

---

### Post by NeoLithium on 2007-06-08
I just tested it a second time.  When you click on organize bookmarks, and make the new bookmark, do you set it up so it looks like this?  (Make sure the new bookmark is actually in the folder as well, and not in the bookmarks toolbar.  The image below is what I used and I tested it out and it worked fine.  Just in case, how are you entering the search in the address bar?

---

### Post by thesonisshining on 2007-06-08
nevermind i forgot to include the 'a' in the search.

it works fine now.

---

### Post by NeoLithium on 2007-06-08
Ok, phew, I was hoping I wasn't just having some freak occurance that wouldnt' work for you.   Glad it all worked out :)

---

### Post by mcmilner on 2007-06-09
I have a slightly different problem:  Yahoo has colonised the search function from the address window.  I have no idea how this happened.  I looked at my bookmarks to see if I could a bookmark such as you described, but the only thing there is the javascript for Google Bookmarks.  Can you tell me how to make Google the default, again?

---

### Post by Outrunner on 2007-06-09
Click on the down arrow button new the Yahoo icon in the search bar and select Google. I think that should do it...

---

### Post by mcmilner on 2007-06-09
The problem isn't the search bar; it's the address bar.

---

### Post by feest on 2007-06-09
thx I didn't know this... i like this feature..

---

### Post by Outrunner on 2007-06-09
> **mcmilner said:**
> The problem isn't the search bar; it's the address bar.

Ahh, do you mean you got a Yahoo toolbar by mistake? Well, I think you'll have an option to remove it if you rightclick on it. If not, try right clicking in the vicinity.

---

### Post by mcmilner on 2007-06-09
Think I'd better start, again.  No, I don't have a Yahoo toolbar.  I do have a Google toolbar, which I loaded the other day, but it doesn't show.  I just moved a couple of things, including the Google Bookmark button to the main Firefox toolbar and then hid the Google Toolbar.

A couple of days later -- I have no idea why or where it came from, although I was trying to get help from Yahoo groups -- Yahoo had become the default search engine for Firefox.  

I know that I can choose any search engine I like from the search engine box.  What I'm talking about is what the other guy was talking about:  I want to be able to type search terms into the address bar.  As a default with Ubuntu, you do that and Google does the search.  I've now got Yahoo doing the search.

---

### Post by mcmilner on 2007-06-11
And here is the answer. I went to my Preferences in my Firefox profile to get rid of the Yahoo stuff, but the correct way to change the default Browser is:

new tab
in address bar, type:  config:about

Change what you like.

---

### Post by avantgardaclue on 2007-06-15
Being based in the UK i would like my firefox google search to default to google.co.uk and not the US oriented google.com.

Can't see how... is it possible?

thanks

---

### Post by mcmilner on 2007-06-15
I knew my research would come in handy.  There are three ways, although i'm not sure how the first one works.

1) New tab / type "about:config" in the address bar (without ") / find Browser.Search.SelectEngine.
   Unfortunately, I don't know what to type there  You might try Google.co.uk 
2)Directly change the Firefox Preferences.js file

Recommended:

3) Load the Firefox Toolbar.  It has a UK option and lots of other neat stuff.  I've combined the Google and Firefox Toolbars and love the choice of options.

---

### Post by avantgardaclue on 2007-06-15
Thanks for the reply, hmmmm....

>>1) New tab / type "about:config" in the address bar (without ") / find Browser.Search.SelectEngine.<<

Went there, couldn't see "Browser.Search.SelectEngine"...

>>2)Directly change the Firefox Preferences.js file<<

Not sure where i can find that, did a Yelp search, still nothing.

>>3) Load the Firefox Toolbar. It has a UK option and lots of other neat stuff.<<

Really loath to add any more toolbars as i have a pretty well tuned version of swiftfox, so thanx for that idea.

I think i would like to pursue your idea 1 most, so many thanks for the ideas.

Simon
England

---

