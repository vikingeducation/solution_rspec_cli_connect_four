solution_tdd_connect_four
=========================




## Overview

This is most likely the first time you've gotten to test an application that you've written yourself! You most likely saw a lot of ways you could improve your code to make testing an easier process. You're probably thinking a lot about how this project will change the way you code in the future and that's a good thing!


## Reviewing Your Solution

While reviewing your solution you should ask yourself the following questions:

* How did you set up tests for your "Play" method?
* Did you use stubs? Or did you get around this another way?
* Did you test only your public methods? Did you test your private methods?
* How would you argue that you're testing your private methods when you test the public ones?
* How easy or difficult was it for you to test various conditions based on multiple game states?
    - Winning game state?
    - Edge cases?
    - How could this be made easier?
    - If you pass the board state as an initialization variable, do you see how testing becomes way easier?


## Key Tips and Takeaways

1. **Passing state on initialization makes testing easier.** If you did not pass the board state to your game on initialization you probably had a difficult time testing various edge cases for win conditions. To avoid this, allow your board to take a state in the `initialize` method.

    ```ruby
    # board.rb
    class Board
      def initialize( board = nil )
        # Remember the ||= trick? It sets the
        # variable to the new value unless it already
        # has a value of its own.
        # It's obviously not *actually* necessary here.
        @game_board ||= board
      end
      ...
    end
    ```

1. **If you tested game play, you must mock input with stubs.** Command-line games require mock input to STDIN. This is done using stubs. If this is unfamiliar to you don't worry, we'll be covering this at length. The gist of it is that you control the return value of `gets` to be exactly what your test requires. You can imagine how useful this is for a command-line game. Here is an example:

```ruby
it "sets player color" do

  # Here we tell RSpec that the instance of
  # `game` will have `gets` called inside it
  # and we want that call to return "r"
  # 
  # Then our game can execute without stopping
  # mid test for manual input
  allow(game).to receive(:gets).and_return("r")
  game.color_prompt
  expect(game.player_1.color).to eq("R")
end
```




## Good Student Solutions

* [Jeff Gisin's Solution](https://github.com/jgisin/project_cli_connect_four)
* [Justin Mullis's Solution](https://github.com/nonadmin/project_ruby_game_center/)

