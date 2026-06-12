---
title: "vfork"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Rij on 2007-09-04
This is a C++ question.
I am building this system which has 3 classes and a main. From a method in one of the classes, I want to execute a different program.

So lets say I have:
1) A file node.h which looks like this:
class C_node {
public: 
C_node(); ~C_node();
 .....
}

2) From within the file node.cc, I want to execute a program a.out
...
bool C_node::execute() {
	pid_t pID = vfork();
	int *status;
	if (pID == 0) {
		execv("./a.out", ARGV);
	}
	else waitpid(0, status, WUNTRACED);
	if (WIFEXITED(*status)) return true;
	else return false;
}

I get a Seg fault when I execute this:
Program received signal SIGSEGV, Segmentation fault.
0x00018b78 in C_node::execute (this=Cannot access memory at address 0x44
) at node.cc:27
27              pid_t pID = vfork();

Can anyone please help? Is there a better way of doing what I am trying to achieve?

Thanks in advance.

---

### Post by aquavitae on 2007-09-04
How do you call C_Node::execute()?  Can you post the code where you call it.  Btw, I assume you do define it in the header...

If you just want to execute a program I think there is another simpler command, but I can't remember what it is - something like system()... You'll have to look at the docs, or try google to see if you can find it.

---

