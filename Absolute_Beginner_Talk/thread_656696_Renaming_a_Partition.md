---
title: "Renaming a Partition"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2008-01-02
As the topic title says, I need to rename a partition.

Also, is it necessary to have a swap partition on a USB drive formatted to ext3 or any other type of partition besides the main?

---

### Post by bindatype on 2008-01-02
OK, I have some questions first. Are you using UUIDs or physical labels? Also, what are you changing and to what? 

Regarding swap, you dont want to format swap as ext3...you format swap as swap. Do you have a swap partition already? Check it with this command
```

top

```

---

### Post by Cheese Roller on 2008-01-02
I want to change the name of the parition that is displayed when it is mounted. Like let's say I want to name it "My Files". That's what I want the mounted drive to display as.

---

### Post by Cheese Roller on 2008-01-02
Where it is normally read "disk"

---

