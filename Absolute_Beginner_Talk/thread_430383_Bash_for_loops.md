---
title: "Bash for loops"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by haelters on 2007-05-02
I have a small scripting issue. Let me first put you in the (simplified) picture: I have a directory with some files in it:

```

total 0
-rw-r--r-- 1 manfred manfred 0 2007-05-02 09:44 boem
-rw-r--r-- 1 manfred manfred 0 2007-05-02 09:40 hello
-rw-r--r-- 1 manfred manfred 0 2007-05-02 09:40 hello 1

```

now I want to write a for loop for a selection of those files (determined by the find command). So I launch the following command:

```

for i in $(find ./test -name 'he*') 
do
  echo $i
done

```

the result is:
```

./test/hello
./test/hello
1

```
 
and not my wanted result:
```

./test/hello
./test/hello 1

```

What must I do so that the for statement does not break up my filenames with a space in them ? Must I change the IFS Variable ?

---

### Post by jyba on 2007-05-02
You need to protect the white space with double quotes. 

```

for i in "$(find ./test -name 'he*')"
do
  echo "$i"
done
```

---

### Post by haelters on 2007-05-02
Thanks !!

I tought I had tried that...

---

