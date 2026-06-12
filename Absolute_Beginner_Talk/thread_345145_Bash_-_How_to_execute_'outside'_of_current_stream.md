---
title: "Bash - How to execute 'outside' of current stream"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by deadimp on 2007-01-23
Is there a way to execute a program 'outside' of a bash program, so that the program is no longer dependent upon bash itself? (Similar to Win32 VB Shell function)

---

### Post by moshuptrail on 2007-01-23
Use nohup <command> &

the nohup executes the command so you can exit without it dying, but it won't give you the $ prompt back
the & at the end gives you the $ prompt

When you log out it will warn that you "have jobs running"
just log out again.  they'll live on

---

### Post by 23meg on 2007-01-23
It will help clarify what you mean by "outside" and "dependent" if you state what exactly you're trying to accomplish.

---

### Post by deadimp on 2007-01-23
By 'outside,' I simply mean to redirect the I/O streams to something other than the terminal, and the terminal would continue to act normally, as though the process had already ended (I will still be able to use the prompt).
What **moshuptrail** has suggested works, since I can close the terminal independent of the program, and I've tried appending the '&', but I don't get the prompt back.
EDIT: Scratch that, I get input back. It was just that it didn't print SP1 ("$") out after executing the program.
I'm asking this because I want to be able to spawn multiple programs from a single terminal, and later close the terminal if need be.

Thanks!

---

