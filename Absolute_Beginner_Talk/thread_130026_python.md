---
title: "python"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by Ubuntuud on 2006-02-15
Hi, I got some .py files but I do not know how to activate/open them... Thanks.

---

### Post by Gimbo on 2006-02-15
I think I've read on these forums somewhere that you can run them by dragging them onto an open terminal window. There's probably a way to do it through the right-click menu as well.

---

### Post by Ubuntuud on 2006-02-15
It isn't working... Any other ideas?

---

### Post by xtacocorex on 2006-02-15
Depending on the first line in the Python script, you can either do:
```
python scriptname.py
```
or
```
./scriptname.py
```

Both are at the command line. The second case will only work if the first line in the file is
```
#!/usr/bin/python
```
The first method should work even if the file has the above first line in it.

You also need to make sure the scripts are able to be executed:
```
chmod +x scriptname.py
```

Hope this helps.

---

### Post by Ubuntuud on 2006-02-15
I allready tried the first one, but I'll go and try the other three... Thanks

---

### Post by steve.horsley on 2006-02-15
The first one is the one that is cersain to work. So if it doesn't, you should try telling us what error message you get, or in what other way it "doesn't work".

---

### Post by Ubuntuud on 2006-02-15
I got it working. The problem was that I typed "python /bla/bla/bla/filename.py" instead of "cd /bla/bla/bl" and "python filename.py".

---

