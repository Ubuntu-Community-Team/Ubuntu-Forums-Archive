---
title: "Making a small script, help"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by aswells on 2006-11-29
I am trying to make a little script that runs the following commands in the terminal 
```

cd ~/.wine/drive_c/Program\ Files/Steam/
WINEDEBUG="-all" nice -n -20 wine explorer /desktop=foo,800x600 Steam.exe
```

I tried putting it in a plain text file. Is there an extension I need to put on the file name?

Thanks

---

### Post by bodhi.zazen on 2006-11-29
> **aswells said:**
> I am trying to make a little script that runs the following commands in the terminal 
```

cd ~/.wine/drive_c/Program\ Files/Steam/
WINEDEBUG="-all" nice -n -20 wine explorer /desktop=foo,800x600 Steam.exe
```

I tried putting it in a plain text file. Is there an extension I need to put on the file name?

Thanks

plain text is fine. You need to make it executable:```
chmod a+x <file_name>
```

To run, type the full_path/to/<file_name>

Or if it is in your current directory, ./<file_name>

to add to your menu/icon/launcher use the command:```
bash full_path/to/file
```

<file_name> = what ever you called this script...

---

### Post by aswells on 2006-11-29
That did the trick, thanks! I used bash to link the script to a launcher, everything works great.

---

