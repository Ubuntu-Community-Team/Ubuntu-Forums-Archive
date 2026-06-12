---
title: "How to search for files"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by HareBall on 2006-10-07
How do you do a search? I am looking for some files I downloaded and tried to use Search, but it always comes up empty. They are some mp3 files and I'm not sure where it put them:confused:  I know I should have paid better attention when I did it:( 
Isn't there a way to do this from a terminal?
Larry

---

### Post by zappa on 2006-10-07
Be sure not to search on desktop, unlike certain software, in Ubuntu it is NOT the top layer, use 'file system'

---

### Post by HareBall on 2006-10-07
> **zappa said:**
> Be sure not to search on desktop, unlike certain software, in Ubuntu it is NOT the top layer, use 'file system'

I have tried 'file system" and any other partition except windows. No help.
I'll see what else I find to try.
Thanx,
Larry:confused:

---

### Post by Anonii on 2006-10-07
Use the locate command.

If you dont remember the exact name of the mp3, you obviously cant use the:
*locate <exact_filename>.mp3*
command.

So you have to do this:

**locate *.mp3 | grep <a word from the song>**

Which will search for everything with the mp3 extension and will filter out the results with the word you entered.

---

### Post by dalee on 2006-10-07
Hi,

Two terminal commands you can use to search are:

user-desktop:~$ whereis filename

or

user-desktop:~$ slocate filename

dalee

---

### Post by CatKiller on 2006-10-07
You could try a ```
sudo updatedb
``` before you search, also.

---

### Post by Marsolin on 2006-10-07
You can also use the find command. Run "man find" to see the usage.

---

### Post by deadgobby on 2006-10-07
> **HareBall said:**
> How do you do a search? I am looking for some files I downloaded and tried to use Search, but it always comes up empty. They are some mp3 files and I'm not sure where it put them:confused:  I know I should have paid better attention when I did it:( 
Isn't there a way to do this from a terminal?
Larry
 You say you DL mp3's. Are they from like Limewire, Frostwire, GTK. Myspace, or other websites? If on p2p programs. It could be save in 
Places>Home Folder>Shared or GTK.

---

### Post by HareBall on 2006-10-07
> **deadgobby said:**
> You say you DL mp3's. Are they from like Limewire, Frostwire, GTK. Myspace, or other websites? If on p2p programs. It could be save in 
Places>Home Folder>Shared or GTK.

I used aMule. I changed where the downloads are saved and now can't remember where they were originally.
Larry:confused:

---

### Post by Anonii on 2006-10-07
There were like 7replies before that post. Did you try them? Did they work?

---

### Post by Ayman on 2006-10-07
> **HareBall said:**
> I used aMule. I changed where the downloads are saved and now can't remember where they were originally.
Larry:confused:

aMule saves downloads at /home/*yourusername*/.aMule by default, and you can find out the new path at Preferences (from the aMule toolbar) > Directories.

---

### Post by deadgobby on 2006-10-07
> **HareBall said:**
> I used aMule. I changed where the downloads are saved and now can't remember where they were originally.
Larry:confused:
Shame on you Larry.... I done it to and try the above post. I see that you could of save the mp3's some where in your home folder. Perhaps some thing simple. Like a folder called mp3's
Gobby

---

### Post by Delkster on 2006-10-07
> **Ayman said:**
> aMule saves downloads at /home/*yourusername*/.aMule by default, and you can find out the new path at Preferences (from the aMule toolbar) > Directories.

Ah, and that would probably also explain why the search didn't find them. Files beginning with a dot are generally configuration files and as such they're hidden by default as the user probably doesn't need to have them at hand except at special occasions. AFAIK the Gnome search doesn't look in folders beginning with dots either (with some searches you might easily get a big bunch of configuration files which probably wouldn't be of interest and would thus only serve to clutter the search results).

Actually I don't think it's very smart behaviour to save into hidden folders by default files that the user probably wants to see and handle directly.

---

### Post by zappa on 2006-10-07
> **Delkster said:**
> AFAIK the Gnome search doesn't look in folders beginning with dots either 

Correct, you can ask it in the dropdown-box however.

---

### Post by HareBall on 2006-10-07
> **Anonii said:**
> There were like 7replies before that post. Did you try them? Did they work?

Tried, yes. Work? No.

---

### Post by HareBall on 2006-10-07
> **zappa said:**
> Correct, you can ask it in the dropdown-box however.

What dropdown box? The window I used to search didn't have one. Is there a different search than the one under places? Terminal hasn't been of any use to me for this.

I figured out how to find it. I changed my view to show hidden files. Helps a lot when you can actually see all the files. Still wouldn't find it when I did a search. I had to manually go through the files until I found what I was looking for.
Search so far has not been very helpful:( Maybe when I get more used to using Linux.
Larry, still confused, but learning more evry day;)

---

### Post by zappa on 2006-10-07
Well, you have this little black triangle, click it ;)

---

### Post by traveller on 2006-10-07
With Beagle perhaps? :)

---

### Post by aldegaz on 2006-10-07
Beagle is an excellent option for looking stuff in Ubuntu you just have to:

```
sudo apt-get install beagle
```

---

