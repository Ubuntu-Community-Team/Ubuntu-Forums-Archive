---
title: "WxWidget"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by Yogesh on 2005-12-30
hi,
I am Working on WxWidget library and using wxList collection class,
I want to assign a object of my own class to it when i do like this
class Myclass
{
private yy;
public:
Myclass(int dt)
{
yy=dt;
}
};
wxList mylst;
Myclass a1=new Myclass(10);
mylst.Append(a1);
}
This will give me error can not convert CObject* to MyClass* 
Can you help me to solve yhis problem;

---

