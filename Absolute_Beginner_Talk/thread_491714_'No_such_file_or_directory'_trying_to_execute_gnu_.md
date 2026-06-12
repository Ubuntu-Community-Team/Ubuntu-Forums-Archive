---
title: "'No such file or directory' trying to execute gnu cross-compiler"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by steve_pye on 2007-07-03
I downloaded the GNU Linux->ARM cross-compiler from [http://www.codesourcery.com/gnu_toolchains/arm/download.html](http://www.codesourcery.com/gnu_toolchains/arm/download.html).  This consisted of a xxx.tar.bz2 file.  I used the File Roller Archive Manager to extract all the compiler binaries.  Unfortunately when I try to execute any of the binaries I get the error 'No such file or directory' - here's an example of the error.

root@steve-laptop:/usr/local/ArmGcc/arm-2007q1/arm-none-linux-gnueabi/bin# ls
ar  as  c++  g++  gcc  ld  nm  objdump  ranlib  strip
root@steve-laptop:/usr/local/ArmGcc/arm-2007q1/arm-none-linux-gnueabi/bin# ls -al gcc
-rwxr-xr-x 1 steve steve 180232 2007-05-02 01:06 gcc
root@steve-laptop:/usr/local/ArmGcc/arm-2007q1/arm-none-linux-gnueabi/bin# ./gcc
bash: ./gcc: No such file or directory

I have the AMD64 version of Ubuntu 7.04.  The compiler download was the IA32 GNU/Linux flavour.

Thanks in advance for your help.

---

### Post by KIAaze on 2007-07-03
Isn't that the same as the standard gcc?

You could easily install it from the repositories by installing either "gcc" or "build-essential" to get all necessary things for compiling and linking.

Sourcery G++?
What is this? Do you really need it?
The Eclipse IDE can be installed from the repositories too.

>  Sourcery G++ includes CodeSourcery&#8217;s latest enhancements to the GNU Toolchain
I seriously hope that they respect the GPL license...

That said, your problem is really strange. gcc is there and is an executable file.
I have no idea why it tells you "No such file or directory". O.o

edit:
Ok, I see. I suppose you need this sourcery G++ to work on microcontrollers or something similar. :oops:

re-edit:
I couldn't find anything clear, but they seem to have [contacted RMS directly]("http://gcc.gnu.org/ml/gcc/2001-07/msg01363.html") so I don't think there's any problem. ^^
They even seem to work very closely with the gcc team. :)

---

### Post by steve_pye on 2007-07-18
I've since discovered that any executable file that's extracted from a zipped up archive is not 'findable' by my bash shell.  Again, I can see the file, I can see that it has its executable mode bits set, I can force the search path by specifying ./, yet I still get 'No such file or directory trying to execute ...'.    Any ideas?  Thanks.

---

### Post by KIAaze on 2007-07-18
That's really strange. O.o

Is it the same if you create an executable yourself?
```
touch foo
chmod 755 foo
./foo

```

And if you try to execute it as root?
```
sudo ./foo
```

Does it also happen with files extracted from a tar.gz?

"unzip" has the following options:
>        -a     convert text files.  Ordinarily all files are extracted exactly as they are stored (as ``binary'' files).  The -a option causes files iden-
              tified by zip as text files (those with the `t' label in zipinfo listings, rather than `b') to be automatically extracted as such, convert-
              ing line endings, end-of-file characters and the character set itself as necessary.  (For example, Unix files use line feeds (LFs) for end-
              of-line  (EOL)  and  have  no  end-of-file (EOF) marker; Macintoshes use carriage returns (CRs) for EOLs; and most PC operating systems use
              CR+LF for EOLs and control-Z for EOF.  In addition, IBM mainframes and the Michigan Terminal System use EBCDIC rather than the more  common
              ASCII  character  set,  and NT supports Unicode.)  Note that zip's identification of text files is by no means perfect; some ``text'' files
              may actually be binary and vice versa.  unzip therefore prints ``[text]'' or ``[binary]'' as a visual check for each file it extracts  when
              using the -a option.  The -aa option forces all files to be extracted as text, regardless of the supposed file type.

       -b     [general] treat all files as binary (no text conversions).  This is a shortcut for ---a.

       -b     [Tandem]  force  the creation files with filecode type 180 ('C') when extracting Zip entries marked as "text". (On Tandem, -a is enabled by
              default, see above).

       -b     [VMS] auto-convert binary files (see -a above) to fixed-length, 512-byte record format.  Doubling the option (-bb) forces all files  to  be
              extracted  in this format. When extracting to standard output (-c or -p option in effect), the default conversion of text record delimiters
              is disabled for binary (-b) resp. all (-bb) files.


Maybe you should try one of them. I've seen the "-a" option used in scripts personnally, maybe it will work, altough the "-b" option would make more sense here.
There are also a lot of other options and also examples in the manual:
```
man unzip
```

---

