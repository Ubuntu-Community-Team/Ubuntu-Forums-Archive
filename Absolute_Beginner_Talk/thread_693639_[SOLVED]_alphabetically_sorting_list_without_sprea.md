---
title: "[SOLVED] alphabetically sorting list without spreadsheet"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2008-02-11
I might be missing something very simple here, but I can't seem to find a way of sorting a 2 (maybe 3) column list by alphabetical order of the entries in the first column. I know I can just put it in a spreadsheet, but I'm hoping for a simpler way, like a table in a word processor or something like that.
Any ideas?

---

### Post by hyper_ch on 2008-02-11
where do you want to list that? in what program?

---

### Post by pt_lam on 2008-02-11
I think spreadsheet is just the fastest and easiest way to do so.

---

### Post by hyper_ch on 2008-02-11
or a php script or this or that... but he gives not information at all.

---

### Post by kleo skywalker on 2008-02-11
I'm trying to make a list of my books.
Now, I know I can use something like Alexandria, and I know I can put it in a spreadsheet, but I was just wondering if there's any way to just put it in a table in a word processor and sort it (or something similar).
On a different but related note, I'm just installing Alexandria to try it out. After I add my book collection, can I generate a list of some kind  - a spreadsheet or document - as a back-up?
Thanks.

---

### Post by ByteJuggler on 2008-02-11
If it was a simple text file, with columns seperated by tabs (say), then you can just use the builtin "sort" command to sort the lines in the file alphabetically.

E.g.

```
sort myfile.txt > newfile.txt
```

Sorted contents in "newfile.txt" after executing command.

Edit: If you're feeling really fancy, you can put the data into an XML text file, then write some XSLT so your browser will automatically sort the data using the XSLT instructions when you view the file... :-)  If you're really interested I can probably try to cook up an example sometime....

---

### Post by kleo skywalker on 2008-02-11
> **ByteJuggler said:**
> If it was a simple text file, with columns seperated by tabs (say), then you can just use the builtin "sort" command to sort the lines in the file alphabetically.

E.g.

```
sort myfile.txt > newfile.txt
```

Sorted contents in "newfile.txt" after executing command.

Edit: If you're feeling really fancy, you can put the data into an XML text file, then write some XSLT so your browser will automatically sort the data using the XSLT instructions when you view the file... :-)  If you're really interested I can probably try to cook up an example sometime....

Wow, thanks but I was looking for simpler than spreadsheet!
I suppose I'll just go with spreadsheet.

---

### Post by LowSky on 2008-02-11
Alexandria is a great program.. it allows you to enter books by ISBN which is such a time saver for me.

---

### Post by kleo skywalker on 2008-02-11
> **LowSky said:**
> Alexandria is a great program.. it allows you to enter books by ISBN which is such a time saver for me.

I tried Alexandria and it really is something. It even exports libraries as .csv files, so my requirements are pretty much taken care of. Pity it doesn't import from .csv files. 
I would really like a way to add more online information providers though. And a way to back up my libraries because I added quite a few books manually, and even looked up cover images.
Should I start a separate thread about this?

---

