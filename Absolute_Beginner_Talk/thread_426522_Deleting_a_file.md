---
title: "Deleting a file"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Ahunt on 2007-04-28
Hi there:

I just want to find out what the sudo command is to delete a file.

Adam

---

### Post by taurus on 2007-04-28
```
sudo rm filename
```

---

### Post by benfindlay on 2007-04-28
I believe its ```
sudo rm [filename]
```

Hope this helps!

---

### Post by Ahunt on 2007-04-28
Do you need to specify the location or just the file name?

Adam

---

### Post by taurus on 2007-04-28
If you are in the same directory where the file is, then you just use the filename.  But if you are in another directory, then you need to specify the exact location--path.

---

### Post by benfindlay on 2007-04-28
if you're already in the folder location you just need to file name, otherwise you need to put the file location in, such as ```
cd Desktop
```

---

### Post by Ahunt on 2007-04-28
Sorry to ask such basic questions - I am on day five on Ubuntu.

By "in the same directory" do you mean have the folder open so you can see the file you want to delete and then open a terminal at that point? Or am I off base?

Adam

---

### Post by benfindlay on 2007-04-28
you need to navigate in terminal to the location, so can I ask where your file is stored?

its simply a case of typing ```
cd file/location
``` into the terminal

---

### Post by taurus on 2007-04-28
If you see that file with nautilus, right click on the file and remove it from there.  Then, empty your trash bin and that baby is gone.  However, if you want to remove it from a terminal, then you would do something like, assuming the file is in ~/Desktop/abc.tar.gz

```
cd ~/Desktop
rm abc.tar.gz
```

---

### Post by Ahunt on 2007-04-28
Thank you both very much - that was very helpful!

My next Ubuntu adventure is going to be trying to connect to the internet using an external hardware modem, after giving up on the internal soft modem over lack of a driver. If it doesn't go smoothly I may end up in a new thread.

Thanks again!

Adam

---

