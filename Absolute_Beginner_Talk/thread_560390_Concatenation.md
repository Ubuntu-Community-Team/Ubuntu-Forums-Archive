---
title: "Concatenation"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by jbMSU on 2007-09-26
I'm assuming this is a newbie enough question to belong in this section.

How would I read in names from a file and then concatenate the first letter of the first name with the last name?

Example:
John Doe -> jdoe

---

### Post by justleen on 2007-09-26
oeps, mis read!

---

### Post by jbMSU on 2007-09-26
Input format:

John Doe
Jo Sixpack
Terry Griffin
etc.

---

### Post by Henry Rayker on 2007-09-26
are you looking to do this with perl or with another scripting language?

Also, should the output be in a new file, or just overwrite the old file? Can it be expected that there will definitely be only a first name, space, last name, new line, or is that up to the script to ensure?

---

### Post by jbMSU on 2007-09-26
I want to script this in BASH.

---

### Post by justleen on 2007-09-26
cat fileswithnames |  [COLOR="SeaGreen"]sed 's/[/COLOR][COLOR="Blue"]\(^[a-zA-Z]\)\([a-zA-Z]*\)\( \)[/COLOR][COLOR="SeaGreen"]/\1/'[/COLOR]  > newfilewithnames

for readabilty:

sed 's/                       
->  sed substitute

\(^[a-zA-Z]\)           
->  the \( is for e literal ( and ), so it will look for the string inside (). in this case,  find the first alpabethic char  (the ^is the beginning of the line)

\([a-zA-Z]*\)                 
-> get the rest of the first word

\( \)                                 
-> get the space

/                                       
-> sed delimiter

\1                                   
-> replace the found string with "\1" which means the first found string.. (your looking for three strings here, first char, rest of the word, and the space each are placed in "memory"and can be accessed with \1 \2 \3)  \1 in this case is the first letter

/'                                       
-> sed delimiter


hmmm... still not readable :))

---

