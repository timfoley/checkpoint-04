# Checkpoint 04

> If you have not completed the survey yet,
please do so by the end of the day!

## Instructions

1. Fork this repo
2. Clone your fork
3. Fill in your answers by writing in the appropriate area, or placing an 'x' in
the square brackets (for multiple-choice questions).
4. Add/Commit/Push your changes to Github.
5. Open a pull request.

> **Note**: Only place your answer between backticks. Don't modify the backticks,
or the language specifier after them.

## Ruby Basics & Enumerables (meets Beauty and the Beast)

### Question 1

Define a method called `offer_rose`, which should take one argument named `person`.

When called the method should `puts` "Would you take this rose, `person`, in exchange for giving an old beggar woman shelter from the bitter cold?"

Demonstrate calling the method, passing in "young prince" as the argument.

Write your code here:
```ruby
def offer_rose(person)
  puts "Would you take this rose, #{person}, in exchange for giving an old beggar woman shelter from the bitter cold?"
end

offer_rose("young prince")
```

### Question 2

Assume the following hash:

```ruby
town = {
  residents: ["Maurice", "Belle", "Gaston"],
  castle: {
    num_rooms: 47,
    residents: "Robby Benson",
    guests: []
  }
}
```

Using Ruby, remove Belle from the town residents, and
add her to the list of guests in the castle.

Write your code here:
```ruby
town[:castle][:guests] << town[:residents].delete_at(1);
```

### Question 3

Assume you have an array of strings representing friend's names:

```ruby
friends = ["Chip Potts", "Cogsworth", "Lumière", "Mrs. Potts"]
```

Using `.each` AND string interpolation, produce output (using `puts`) like so:

```
Belle is friends with Chip Potts
Belle is friends with Cogsworth
Belle is friends with Lumière
Belle is friends with Mrs. Potts
```

Write your code here:
```ruby
friends.each do |friend|
  puts "Belle is friends with #{friend}"
end
```
## Ruby OOP (meets Lion King)

### Question 4

Create ruby classes for `Animal` and `Lion`.
Each `Animal` should have:

- a `name` attribute
- a `greet` instance method
- Getter and setter for `name`

Create a new `Animal` instance with the name "Pumba"

Make the `Lion` inherit from the `Animal` class.
The `Lion` class should have a `pack` class variable that holds references to each instance created.

Each lion should have:
- a `king` attribute which is a boolean
  - If the instance's `name` is `Simba` make the `king` attribute true

Create a new lion instance with the name `simba`

```ruby

# not sure why this isn't working when I test. I get argument errors, expected 0, got 1 any time I try to make a new animal or Lion...
class Animal
  attr_accessor :name,
  def initialize(name)
    @name = name
  end

  def greet
    puts "Hi there! I'm #{@name}"
  end
end

class Lion < Animal
  @@pack = []
  attr_accessor :name, :king
  def initialize(name)
    super(name)
    if @name == "Simba"
      @king = true
    end
    @@pack << self
  end
end

pumba = Animal.new("Pumba");


```

## SQL, Databases, and ActiveRecord (meets Aladdin)

### Question 5

Describe what an ERD is, and why we create them for applications. Also give an
example what the attributes and relationships might be for the following
entities (no need to draw an ERD):
* Genie
* Lamp
* Person
* Pet

Your answer:
```
An ERD is an "Entity Relationship Diagram". ERDs are meant to describe how the various elements in an application are associated with each other. Creating an ERD will make it much easier to work with a large program, because you will have a good idea of the various classes, etc. you will have to write before you start coding.

One lamp (color, size) has one genie (color, size, temperament, wishes_granted), and only one person at a time. One person (name, protagonist(true/false), catchphrases) can have many lamps. Many pets can have many people.
```

### Question 6

Describe what a schema is, and how we represent a one-to-many relationship in a
SQL database. If you need an example, you can use: people and wishes
(one-to-many).

Your answer:
```
A schema is the high-level collection of tables and columns that make up a database. It includes information on the relationships between entities (one-to-many, many-to-many, etc.).


I imagine there are a few ways you could add wishes to a database: one table called `wishes` for everyone which would have a column connecting each wish to a person using a foreign id. Alternatively, each person could get their own wishes table. Right now, I'm not too sure on the advantages of one vs another (and with Active Record, it seems like you can kinda have boooth?)


```
