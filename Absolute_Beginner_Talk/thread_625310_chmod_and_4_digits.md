---
title: "chmod and 4 digits"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2007-11-27
I've seen chmod 0777 many times. And now, on page 49 of "Using Samba 3rd Edition" (O'Reilly) it says > chmod 1777 /exports/tmpWhat is that fourth digit supposed to represent. In chmod 762, the 7 is Owner, the 6 is group, and the 2 is User**s**, right? So what would the 1 be in chmod 1762 ????

---

### Post by spiderbatdad on 2007-11-27
Wikipedia

# chmod 0755 file &#8211; equivalent to u=rwx (4+2+1),go=rx (4+1 & 4+1). The 0 specifies no special modes.
# chmod 4755 file &#8211; the 4 specifies set user ID.

Here is a summary of the meanings for individual octal digit values:

1 --x execute 
2 -w- write 
3 -wx write and execute
4 r-- read
5 r-x read and execute
6 rw- read and write
7 rwx read, write and execute

Octal digit values can be added together to make Symbolic Notations:
(4=r)+(1=x) == (5=r-x)
(4=r)+(2=w) == (6=rw-)
(4=r)+(2=w)+(1=x) == (7=rwx)

Here is a summary showing which octal digits affect permissions for user, group, and other:

    * UGO = User, Group, Other
    * 777 = "-rwxrwxrwx" = rwx for all
    * 754 = "-rwxr-xr--" = rwx for owner, r-x for group, r-- for other
    * 124 = "---x-w-r--" = x for owner, w for group, r for other

[edit] Octal notation and additional permissions

There is also a four-digit form of octal notation. In this scheme, the standard three digits described above become the last three digits. The first digit represents the additional permissions. On some systems, this first digit cannot be omitted; it is therefore common to use all four digits (where the first digit is zero).

This first digit is also the sum of component bits:

    * The setuid bit adds 4 to the total,
    * The setgid bit adds 2 to the total, and
    * The sticky bit adds 1 to the total.

The example from the Symbolic notation and additional permissions section, "-rwsr-Sr-x" would be represented as 6745 in four-digit octal. In addition, the examples in the previous section would be represented as 0755, 0664, and 0500 respectively in four-digit octal notation.

[edit]

---

### Post by ant2ne on 2007-11-28
"The first digit represents the additional permissions." 

What additional permissions?

---

