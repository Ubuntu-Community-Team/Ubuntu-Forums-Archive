---
title: "Pdftk"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by indie56 on 2007-05-14
Hello
I used Synaptic to install pdftk. I cannot locate it anywhre. 
Help pl.

---

### Post by Happy_Man on 2007-05-14
Open up a terminal (System --> accessories --> Terminal) and enter:
```
pdftk
```

That will start it. Next time you log in, it should show up in the menus.

---

### Post by earobinson on 2007-05-14
have you tryed typing pdftk in the terminal?

---

### Post by indie56 on 2007-05-14
I typed pdftk in treminal to get

SYNOPSIS
       pdftk <input PDF files | - | PROMPT>
            [input_pw <input PDF owner passwords | PROMPT>]
            [<operation> <operation arguments>]
            [output <output filename | - | PROMPT>]
            [encrypt_40bit | encrypt_128bit]
            [allow <permissions>]
            [owner_pw <owner password | PROMPT>]
            [user_pw <user password | PROMPT>]
            [flatten] [compress | uncompress]
            [keep_first_id | keep_final_id] [drop_xfa]
            [verbose] [dont_ask | do_ask]
       Where:
            <operation> may be empty, or:
            [cat | attach_files | unpack_files | burst |
             fill_form | background | stamp | generate_fdf
             dump_data | dump_data_fields | update_info]

       For Complete Help: pdftk --help
pdftk does not show up anywhere

---

### Post by earobinson on 2007-05-14
so its looking for an input file, type ```
man pdftk
``` in the terminal this will tell you how to work it.

---

### Post by indie56 on 2007-05-14
man gives the way to use it. Is there a GUI ? I am no good at terminal commands. Also it does not show up in the Applications.

---

### Post by earobinson on 2007-05-15
It seems like its a command line program sorry.

---

