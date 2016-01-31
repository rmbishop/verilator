The binary used in these examples was
found in "verilator-3.841.7z", which was located here:
http://www.veripool.org/boards/1/topics/945-Verilator-Verilator-binaries-for-windows]]


Example 1:  Hello World


1)Create a project on your desktop named "verilator_example"

2)Open a command prompt in the "verilator_example" folder.

3)Create the following file in a text editor, and name in example1.v

   module MyRandomModuleName;
         initial begin $display("Hello World"); $finish; end
   endmodule


4)Create the following file in a text editor, and name it example1.cpp


   #include "Vexample1.h"
   #include "verilated.h"
   int main(int argc, char **argv, char **env) {
       Verilated::commandArgs(argc, argv);
       Vexample1* top = new Vexample1;
       while (!Verilated::gotFinish()) { top->eval(); }
       delete top;
       exit(0);
   }

5)Generate a cpp file from example1.v, by typing the following:

   verilator example1.v --cc


6)Then build an executable by typing the following (all on one line).  Replace
  "verilator-3.841" with the correct folder name if version 3.841 is not what
   you have installed.

   g++ -oexample1.exe example1.cpp obj_dir/Vexample1.cpp obj_dir/Vexample1__Syms.cpp "C:/Program Files (x86)/verilator-3.841/include/verilated.cpp" -Iobj_dir  -I"C:/Program Files (x86)/verilator-3.841/include/" 


7)Type "example1.exe".  The result printed to the console should be:

   Hello World
   - example1.v:2: Verilog $finish

