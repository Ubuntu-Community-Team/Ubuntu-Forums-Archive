---
title: "Function Program Game"
date: 2011-01-15
forum: Cafe Games
---

### Post by slooksterpsv on 2011-01-15
For Programmers or people who know programming - sorry seems unfair, but let's just roll with it cause I want to see how this works.

**GAME RULES**
1. You create a function or modify a function to include your function.
2. You continue to build until you have the program do what you want.
3. 1 function per post/1 mod + 1 function per post
4. No double-posting e.g. I can't post twice.
5. Someone can post a fix for your function if your function includes errors.
6. After a couple of pages I'll take all the responses and compile the program and see what it does.

**EXAMPLE**
I post:
```

int main()
{
 startProg();
 return 0;
} //I modified 1 function (in this case int main)

void startProg()
{
 cout << "Hello I'm a startProg() function!";
}

```

The next person may modify int main to include it to run their function and add their function or even extend/mod my function do do more things. That would count as one item.

Not sure if it makes sense, if not let's just continue with how we're doing it. I want to see if we can make a fully functional program.

**START!**
Here's my entry:
```

int main()
{
 int x = 0;
 showValue(x);
 return 0;
}

void showValue(int a)
{
 cout << a << endl;
}

```

---

### Post by DOSIX on 2011-01-16
```

//i'm putting the prototypes just for easy reference
void showValue(int a);
void AddressOf(int a);

int main()
{
 int x = 0;
 cin >> x; //makes it a bit more interesting because if not it's always 0
 showValue(x);
 AddressOf(x);
 return 0;
}

void showValue(int a)
{
 cout << a << endl;
}

void AddressOf(int a)
{
    int *b = &a
    cout << "The Address of ", a, "is: ", b << endl;
}

```

---

### Post by rafalcieslak on 2011-02-26
```

//i'm putting the prototypes just for easy reference
void showValue(int a);
void AddressOf(int a);
int hideValue();

int main()
{
 int x = 0;
 x = hideValue(); //makes it a bit more interesting because if not it's always 0
 x++;
 showValue(x);
 AddressOf(x);
 return 0;
}

void showValue(int a)
{
 cout << a << endl;
}

int hideValue()
{
 int x;
 cin >> x;
 return x;
}

void AddressOf(int a)
{
    int *b = &a
    cout << "The Address of ", a, "is: ", b << endl;
}

```

---

