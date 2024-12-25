include <stdio.h>
#include <string.h>

// Define structure for movie
typedef struct {
    char name[50];
    char timing[10];
    int price;
    int seats;
} Movie;

// Function to display movie details
void displayMovieDetails(Movie movie) {
    printf("Movie Name: %s\n", movie.name);
    printf("Timing: %s\n", movie.timing);
    printf("Price: Rs. %d\n", movie.price);
    printf("Seats Available: %d\n", movie.seats);
}

// Function to book ticket
void bookTicket(Movie *movie, int numSeats) {
    if (numSeats <= movie->seats) {
        movie->seats -= numSeats;
        printf("Ticket booked successfully!\n");
        printf("Total amount: Rs. %d\n", numSeats * movie->price);
    } else {
        printf("Sorry, insufficient seats available.\n");
    }
}

int main() {
    Movie movie;
    int choice, numSeats;

    // Initialize movie details
    strcpy(movie.name, "Avengers: Endgame");
    strcpy(movie.timing, "10:00 AM");
    movie.price = 200;
    movie.seats = 100;

    while (1) {
        printf("1. Display Movie Details\n");
        printf("2. Book Ticket\n");
        printf("3. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                displayMovieDetails(movie);
                break;
            case 2:
                printf("Enter number of seats to book: ");
             scanf("%d", &numSeats);
                bookTicket(&movie, numSeats);
                break;
            case 3:
                printf("Exiting...\n");
                return 0;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    }

    return 0;
}
