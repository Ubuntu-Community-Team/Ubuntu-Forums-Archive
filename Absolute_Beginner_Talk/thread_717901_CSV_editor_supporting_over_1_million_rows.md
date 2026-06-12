---
title: "CSV editor supporting over 1 million rows"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by wednesday allfather on 2008-03-07
I refuse to use M$office 07.  I need to open and edit (very simple changes by row) .csv files.  These files are all business listing for an entire state, so they are very large.

I am not opposed to learning ANY kind of software or interface, as long as I don't have to do this in VMware Windows with Office 07.  I would prefer something user-friendly (GUI with OO or Excel style), but it isn't a deal breaker for me if not.

Thanks in advance, fellow Ubuntu-ers.

---

### Post by Oldsoldier2003 on 2008-03-07
> **wednesday allfather said:**
> I refuse to use M$office 07.  I need to open and edit (very simple changes by row) .csv files.  These files are all business listing for an entire state, so they are very large.

I am not opposed to learning ANY kind of software or interface, as long as I don't have to do this in VMware Windows with Office 07.  I would prefer something user-friendly (GUI with OO or Excel style), but it isn't a deal breaker for me if not.

Thanks in advance, fellow Ubuntu-ers.
wow, huge files... have you even tried to open one in open office?

---

### Post by wednesday allfather on 2008-03-07
Yes, I have.  It doesn't support files of that size.  I need something without a row limit, or very high limit.

---

### Post by Whiffle on 2008-03-07
So, what created the files in the first place?  Why not break them up?

---

### Post by Oldsoldier2003 on 2008-03-07
> **wednesday allfather said:**
> Yes, I have.  It doesn't support files of that size.  I need something without a row limit, or very high limit.

Perhaps import the data into mysql? or is that overkill for what you want to do with the data?

---

### Post by wednesday allfather on 2008-03-07
Yeah, that is overkill.  All I need to do is correct a typo (Kentucky is KE instead of KY) in a single column.  

I have to do stuff like this from time to time, so I was looking for a permanent, lightweight solution.  Anything to keep from having to install Office 07.  It's an OK program, but it is just so big.  Way more than I need.  

As far as my life and job are concerned, this is the only thing I need a spread sheet to do for me.  I care nothing for pivoting, formulas, etc.  I simply need to edit a column.  This is a kinda rare occasion, so I can't prolly find a place to use Excel, or I can install it on my VMWare windows.  I would prolly use SQL before that, however.  

Surely there is something out there for a faithful Linux lover... I couldn't look Gnome in the eyes, knowing I had cheated on her.  :)

Thanks in advance.

---

### Post by Jonne on 2008-03-07
Don't fear the command line, I think you can easily do this with sed (type 'man sed' in the terminal to see what your options are).

Or just open it in a text editor and use find/replace

---

### Post by wednesday allfather on 2008-03-07
Perhaps I should have feared the CL.  Sed isnt going to do the job.  Replacing the state abbr. (KE with KY in this case) is doable, but it replaces all KE's with KY's.  So, if "KE" exists in any other fields, then it is replaced.  

That being said, SED is pretty cool.  I'm happy to know about it's existence.  Thanks, I appreciate the advice and direction.

---

### Post by Jonne on 2008-03-07
with some advanced regexps you should be able to get to the right column, although without a small sample of the file it's hard to show the right course of action.

---

### Post by dcstar on 2008-03-07
> **wednesday allfather said:**
> Yeah, that is overkill.  All I need to do is correct a typo (Kentucky is KE instead of KY) in a single column.  
.........

```
man sed
```

Once you master the find and replace functions it is pretty easy to use, and lightening fast......

Oh, and don't worry about the other data, you want to find ",KY," and replace it with ",Kentucky," - I doubt that you will have too many other fields with ",KY," in your data.

---

