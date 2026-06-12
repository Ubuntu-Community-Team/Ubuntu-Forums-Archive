---
title: "Help compiling graphics card driver from source"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by ErsatzM on 2006-08-02
I've downloaded a driver for my incredibely old pro Savage inegrated gfx card. It came in a .tgz tar file. When i type in ```
tar –zxvf Savage_4.0.3_binary.tgz
```

it says

```
tar: Savage_4.0.3_binary.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

I know I installed build-essentials. What is going on?

---

### Post by croak77 on 2006-08-02
Are you sure it downloaded currectly? Check the file size of the tar.

---

### Post by ErsatzM on 2006-08-02
In Firefox's downloads window it says it finished downloading. The tar size is 60kb.

---

### Post by croak77 on 2006-08-02
Where did you download it to? Are you sure you were in the same directory as the file?

---

### Post by croak77 on 2006-08-02
Also there is xserver-xorg-driver-savage in the repo's.

---

### Post by ErsatzM on 2006-08-02
It's just right here on the desktop. Do I need to type out the whole file path on the command line?

---

### Post by croak77 on 2006-08-02
You need to 'cd' to the directory which contains the driver ie. cd Desktop, But why not use the deb in the repo? I'm pretty sure it's the same thing.

---

### Post by mlind on 2006-08-02
> **ErsatzM said:**
> It's just right here on the desktop. Do I need to type out the whole file path on the command line?

```

tar zxvf ~/Desktop/Savage_4.0.3_binary.tgz

```

---

### Post by ErsatzM on 2006-08-02
Thanks. I didn't know it was in the repo's.

---

