---
title: "spaces in folder names is a problem in terminal?"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by onesojourner on 2006-09-08
I am trying to navigate through my wine folder using the terminal. I am fine through /.wine/drive_c but then when I try to type Program Files it says its not available but running ls says its there. I even tried copying it directly  from the ls output. ](*,)

---

### Post by earobinson on 2006-09-08
Program Files = Program\ Files or you can put it all in quotes. you could also type Program then hit tab and ubuntu will compleat it for you

---

### Post by Iarwain ben-adar on 2006-09-08
Hi,
normally when you have spaces, you can type the location with ""
```
cd "~/.wine/drive_c/Program Files"
```

Or you can just type the capital P, and press tab (then it fills it in for you ;)


Iarwain

---

### Post by Foudre on 2006-09-08
can't remember off top of head but i think using // counts as a space

---

### Post by onesojourner on 2006-09-08
nope neither one of those did it pressing tab after cd P says just types rogram and hitting enter says invalid.

adding " to the end just puts me on the next line with this
>

and then I dont know what to do with that. hitting enter does something like this
>
>
>
ect....

typing cd Program//Files 
also gives me a no such file.

---

### Post by Iarwain ben-adar on 2006-09-08
```
cd Program\ Files/       
```

Try this :D


Iarwain

---

### Post by argie on 2006-09-08
> **onesojourner said:**
> nope neither one of those did it pressing tab after cd P says just types rogram and hitting enter says invalid.

adding " to the end just puts me on the next line with this
>

and then I dont know what to do with that. hitting enter does something like this
>
>
>
ect....

typing cd Program//Files 
also gives me a no such file.

That happens to me when I forget to open the quotes first.

cd "Program Files" works fine. 

Iarwain's solution works perfectly for me too

---

### Post by christhemonkey on 2006-09-08
That should be:
```
cd Program\ Files 
```
Should work if you are indeed in your ~/.wine/drive_c/ directory. (cd ~/.wine/drive_c/)

---

### Post by onesojourner on 2006-09-08
cool thanks guys I am going to go with the "xxxxd xxxx" thats easy to remember.

---

### Post by msandersen on 2006-09-08
> **onesojourner said:**
> adding " to the end just puts me on the next line
Put the *whole* path in quotes (beginning and end), not just a quote at the end, like shown above.

---

