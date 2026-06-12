---
title: "how to redirect output"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-09-07
i am trying to redirect all my compiler errors to a file because there are so many they cant all fit in the terminal. so i try to do 
make install > myfile
and it creates myfile and it has the first line but the rest of the output is still going to the termianl...

anyideas how i can get all the terminal output to the file?
Thanks

or if you know a way to display output but make it so i can pagedown or just see the beginning of this huge output stream.

---

### Post by DSn0wMan on 2006-09-07
Try the ">>" (append) operator.

make install >> myfile

---

### Post by Miademora on 2006-09-07
```
make install > log 2>&1
```

This command redirects standard output and error output into a file.

---

### Post by jinxjinx on 2006-09-08
still no luck i only get the first few lines.

---

### Post by TyphoonJoe on 2006-09-08
Redirect ALL output (stdout and stderr):
```
make install &>/directory/file
```

Redirect STDOUT (aka "normal" messages):
```
make install 1>/directory/file
```

Redirect STDERR (aka "error" messages):
```
make install 2>/directory/file
```

good luck with the compile ^_^

---

