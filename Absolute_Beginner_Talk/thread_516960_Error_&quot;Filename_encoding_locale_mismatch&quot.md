---
title: "Error: &quot;Filename encoding locale mismatch&quot;"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-08-03
GQview error message:

[I]One or more filenames are not encoded with the preferred locale character set. Operations on, and display of these files with gqview may not succeed.
If your filenames are not encode in utf-8, try setting the environment variable G_BROKEN_FILENAMES=1
It appears G_BROKEN_FILENAMES is not set.
The locale appears to be set to "en_US>UTF-8"
(set by the LANG environment variable)
Preferred encoding appears to be UTF-8, however the file: [filename] is NOT encoded in valid UTF-8.[/I]

Not that I understand half of what that means. I'm guessing G_BROKEN_FILENAMES is buried somewhere in Gnome's Configuration Editor.

But perhaps more to the point, I think I'd like to just change any filenames that are not UTF-8 to UTF-8, then I'll have filenames that work across all my programs and filesystems.

So what I'm looking for is a utility to locate all such files. GQview is most unpleasant to use for that task. What are my options here?

(Funny part is the GQview Rename utility has no problem showing me the filenames that GQview says it cannot read...)

---

### Post by apswartz on 2007-08-04
I'm not familiar with the utility you are using.

What types of files are we talking about? Plain Text? RTF? MS Word? OpenDocument? HTML? All of the Above?

---

### Post by ofb on 2007-08-04
> **apswartz said:**
> I'm not familiar with the utility you are using.

I mean whatever GQview is using internally to identify bad filenames, and then offers for renaming. Neither are much good for this.

What happens is you get a dialog like my example when you enter a directory. You only get the dialog once - if you skip it, you have to leave the directory and come back to see it again. Sometimes you have to close and reopen GQview as well. What's more, GQview only identifies one bad filename in the directory - if there are more, you won't find out find out next time you visit. Tedious.

Then it's just as clumsy if you try renaming a non-UTF8 filename - when you delete the offending character to begin replacement, five adjacent characters disappear along with.

So, yes - while GQview does at least tell you it has trouble with non-UTF8, it's not much good for fixing that. 

> What types of files are we talking about? Plain Text? RTF? MS Word? OpenDocument? HTML? All of the Above?

Just filenames. I don't want to change anything within a file.

So what I need is somelike like a Seach I guess. Say, select "show me all non-UTF8 filenames, so I can rename the files in UTF8 characters my programs like."

---

### Post by apswartz on 2007-08-04
Well, I've been thinking about your problem. I thought perhaps a shell script would do it, but I can come up with one. It would probably have to be rather complex.

btw, how did your filenames end up that way?

---

### Post by ofb on 2007-08-04
> **apswartz said:**
> Well, I've been thinking about your problem. I thought perhaps a shell script would do it, but I can come up with one. It would probably have to be rather complex.

Thanks, but please don't put yourself out. What I was hoping was there'd be an existing method or utility that someone could point me to. If there isn't, I'll just weed manually as I come across these gems. They show up as squares in Konqueror.

> btw, how did your filenames end up that way?

They didn't originate with me, so I'm guessing they were written with something other than UTF-8. Seems the offending characters always have umlauts or accents.

The odd part (to me) is some programs don't have trouble showing the original characters. Even in GQview, the internal Rename utility shows you the characters correctly when naming the file you are about to change, yet the characters show up as question marks in the file panel.

---

