---
title: "Need help counting words in a comma separated file"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Diversion on 2007-06-12
I have a file where names, and adresses are separeted bij a comma(,).
I want to count the words inside the document excluding the comma but no luck so far.
What I have:

sort -t , kl4a.txt | wc -w

any help would be appreciated!

---

### Post by yota on 2007-06-12
Hi,

try this one:
```

cat kl4a.txt|tr , ' '|wc -w

```

Hope this helps

---

### Post by sankarv on 2007-06-12
try using tr replacing "," with a " "....

---

### Post by nonovo on 2007-06-12
cat kl4a.txt | perl -nle '$a += scalar(split(",",$_));END{print $a}'

---

### Post by Skrynesaver on 2007-06-12
nonovo, I love Perl, it's a fantastic tool, however there is a *rule*  that you should use the simplest tool for the job. tr & wc are fine for this.

BTW: assignment of an array to a scalar should return a scalar automatically.

---

### Post by Diversion on 2007-06-12
Thank you guys for the quick replies it sure helped me out a lot.

---

