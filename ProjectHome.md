# Protocol Buffers #

**The project is moved to github. Please visit our github page [here](https://github.com/google/protobuf/).**

## What is it? ##

Protocol Buffers are a way of encoding structured data in an efficient yet extensible format.  Google uses Protocol Buffers for almost all of its internal RPC protocols and file formats.

## Download ##

[Download latest releases.](https://github.com/google/protobuf/releases)

## Latest Updates ##

https://github.com/google/protobuf/blob/master/CHANGES.txt

## Documentation ##

[Read the documentation.](https://developers.google.com/protocol-buffers/docs/overview)

## Discussion ##

[Visit the discussion group.](http://groups.google.com/group/protobuf)

## Quick Example ##

You write a `.proto` file like this:

```
message Person {
  required int32 id = 1;
  required string name = 2;
  optional string email = 3;
}
```

Then you compile it with `protoc`, the protocol buffer compiler, to produce code in C++, Java, or Python.

Then, if you are using C++, you use that code like this:

```
Person person;
person.set_id(123);
person.set_name("Bob");
person.set_email("bob@example.com");

fstream out("person.pb", ios::out | ios::binary | ios::trunc);
person.SerializeToOstream(&out);
out.close();
```

Or like this:

```
Person person;
fstream in("person.pb", ios::in | ios::binary);
if (!person.ParseFromIstream(&in)) {
  cerr << "Failed to parse person.pb." << endl;
  exit(1);
}

cout << "ID: " << person.id() << endl;
cout << "name: " << person.name() << endl;
if (person.has_email()) {
  cout << "e-mail: " << person.email() << endl;
}
```

For a more complete example, see the [tutorials](https://developers.google.com/protocol-buffers/docs/tutorials).