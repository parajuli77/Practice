# Practice
hi i am practicing coding
using System;
using System.Text;
namespace SydneyCoffee
{
    class Program
    {
        static void Main(string[] args)
        {
            int n = 5;

            String[] name = new String[n];
            int[] quantity = new int[n];
            String[] reseller = new String[n];
            double[] charge = new double[n];

            double price;
            double min = 9999999;
            String minName = "";
            double max = -1;
            String maxName = "";


            Console.WriteLine("\t\t\tWelcome to sydney coffee program\n");

            for (int i = 0; i < n; i++)
            {
                Console.Write("Enter Customer Name: ");
                name[i] = Console.ReadLine();

                quantity[i] = 0;
                do
                {
                    Console.Write("Enter the amount of Coffee beans bags (bag/1kg) : ");
                    bool correctInput = false;
                    while (!correctInput) // this loop will continue until the user enters a number
                    {
                        correctInput = int.TryParse(Console.ReadLine(), out quantity[i]); // if the parsing was successful it returns true
                        if (!correctInput)
                        {
                            Console.Write("Please enter a number.");
                        }
                    }
                    if (quantity[i] < 1 || quantity[i] > 200)
                    {
                        Console.WriteLine("Invalid Input ! \n Coffee bags between 1 and 200 can be ordered.");
                    }
                } while (quantity[i] < 1 || quantity[i] > 200);
                if (quantity[i] <= 5)
                {
                    price = 36 * quantity[i];
                }
                else if (quantity[i] <= 15)
                {
                    price = 34.5 * quantity[i];
                }
                else
                {
                    price = 32.7 * quantity[i];
                }
                Console.Write("Enter Y to indicate whether you are a reseller, OR enter anything else to indicate that you are not a reseller : ");
                reseller[i] =
Console.ReadLine();
                if (reseller[i] == "Y" || reseller[i] == "y")
                {
                    charge[i] = price * 0.8;
                    reseller[i] = "Yes";
                }
                else
                {
                    charge[i] = price;
                    reseller[i] = "No";
                }
                Console.WriteLine(String.Format("The total sales value from {0} is ${1} ", name[i], charge[i]));
                Console.WriteLine("-------------------------------------------------------------");

                if (min > charge[i])
                {
                    min = charge[i];
                    minName = name[i];
                }

                if (max < charge[i])
                {
                    max = charge[i];
                    maxName = name[i];
                }

                Console.WriteLine("\t\t\t\t\t Summary of the sales\n");
                Console.WriteLine("-------------------------------------------------------------");
                Console.WriteLine("-------------------------------------------------------------");
                Console.WriteLine(String.Format("{0,15} {1,10} {2,10} {3,10}", "Name", "Quantity", "Reseller", "Charge"));

                for (int k = 0; k < i + 1; k++)
                {
                    Console.WriteLine(String.Format("{0,15} {1,10} {2,10} {3,10}", name[k], quantity[k], reseller[k], charge[k]));
                }
                Console.WriteLine("-------------------------------------------------------------");
                Console.WriteLine("-------------------------------------------------------------");

                Console.WriteLine("The customer spending most is {0} is ${1} ", maxName, max);
                Console.WriteLine("The customer spending least is {0} is ${1} ", minName, min);
                //Console.WriteLine("last");
            }

            //Console.Read();
        }
    }
}

