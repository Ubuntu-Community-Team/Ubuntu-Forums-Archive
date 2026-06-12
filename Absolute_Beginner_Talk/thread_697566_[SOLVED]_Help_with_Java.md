---
title: "[SOLVED] Help with Java"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by dwally89 on 2008-02-15
Hi,

I've just started teaching myself Java (I already know VB.NET).

I'm using NetBeans to write/complile/run/etc.

So:
I have a JTextField called TextBox.
However when using the following code to read from the textbox, I get the following error:
"non-static variable TextBox cannot be referenced from a static context".

What does this error mean, and how can I solve it?

Thanks

```

 public static void part6 () {
                String s="";
                
                s=TextBox.getText();
    }

```

---

### Post by zerhacke on 2008-02-15
A static method may not call a non-static method (unless that non-static method is being invoked from an object reference).

---

### Post by dwally89 on 2008-02-15
Please could you explain what that means, and what changes I need to make to my code?

Thanks

---

### Post by zerhacke on 2008-02-15
Let me brush up on my Java and I'll show you how to do what you're trying to do.  If I remember right all you have to do is not declare public as static, but don't quote me on it.

---

### Post by dwally89 on 2008-02-15
That works thanks, but I'm trying to call this from a button using the following, and get the same error when I try and call it from a button:

```

private void Btn6ActionPerformed(java.awt.event.ActionEvent evt) {
       Home.part6();
{

```

How do I solve this?

Thanks

---

