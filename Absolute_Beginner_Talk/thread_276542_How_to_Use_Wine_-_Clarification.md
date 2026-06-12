---
title: "How to Use Wine - Clarification"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by Kevin Funnell on 2006-10-13
Good Afternoon All,

I have read many threads of "How To Use" Wine.  I need clarification on one point.  Do I use Wine to run the file ****.exe, like setup.exe before it has been install in Programs File in Windows or do I use the ***.exe file that has bee installed in the Program Files in Windows.

Thanks, Old Kevin

---

### Post by soc on 2006-10-13
both.

---

### Post by 3rdalbum on 2006-10-13
Just to clarify:

If you have a mounted Windows partition with programs that you've already installed, Wine might have some difficulty running them. You should actually run the installer in Wine, so everything gets installed in the correct locations for Wine to use.

The first time you run the now-installed program in Wine, you should do so from the terminal so you can check for error messages. Error messages can sometimes help you find what "native" DLL files Wine needs.

After you're sure that the program works fine in Wine, you can just open it by double-clicking it.

---

